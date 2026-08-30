# Becoming a Linux kernel contributor

The community does **not** use GitHub pull requests for mainline. You send **plain-text patch emails** generated from Git. The first goal is not a clever feature. It is learning that pipeline with one tiny, correct change.

Read these in the tree (or on docs.kernel.org) before you send anything:

- `Documentation/process/submitting-patches.rst`
- `Documentation/process/coding-style.rst`
- `Documentation/process/email-clients.rst`
- `Documentation/process/submit-checklist.rst`

---

### Step 1: Set up your environment

Use a real Linux install (Ubuntu, Debian, or Fedora). A VM is fine. WSL2 often works for building and formatting patches, but SMTP and full kernel builds are less annoying on a VM or native disk.

**Disk / RAM (what “50GB” actually means):**
- Bare clone of mainline: on the order of 3–6GB.
- After a full build: commonly **20–40GB+** of object files, sometimes more.
- A full compile wants **plenty of RAM** (16GB is comfortable; 8GB will swap).

**1. Install tools**

Debian / Ubuntu:

```bash
sudo apt update
sudo apt install build-essential libncurses-dev bison flex \
  libssl-dev libelf-dev git git-email bc pahole perl python3
```

Fedora:

```bash
sudo dnf groupinstall "Development Tools"
sudo dnf install ncurses-devel bison flex elfutils-libelf-devel \
  openssl-devel git git-email bc pahole perl python3
```

`git-email` is easy to miss and is what provides `git send-email`.

Optional but useful later: `b4` (`sudo apt install b4` / `sudo dnf install b4`, or `pip install --user b4`).

**2. Configure Git with your legal identity**

This is not cosmetic. `Signed-off-by` is the Developer’s Certificate of Origin. Use your **real name** and an email you control. Nicknames and throwaway addresses get patches rejected.

```bash
git config --global user.name "Your Real Name"
git config --global user.email "you@example.com"
```

Use the same address you will send mail from.

**3. Clone mainline**

```bash
git clone https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git
cd linux
```

First clone can take a while (large history). A shallow clone is faster to download but awkward when you need history for `Fixes:` tags and `get_maintainer.pl`; prefer a full clone if you can.

You will work on a **branch**, never directly on `master`.

For many first staging/docs patches, Linus’s tree is enough. For a specific subsystem, the `MAINTAINERS` file lists that maintainer’s tree (`T:` line). Patches against a stale tree get “please rebase” instead of review.

---

### Step 2: Prove you can build (optional for pure docs, required for C)

For a spelling fix in `Documentation/`, you do **not** have to boot a custom kernel. You still want the scripts (`checkpatch.pl`, `get_maintainer.pl`) from a current tree.

`make defconfig` builds a generic config. It proves the compiler works. It is **not** a copy of the kernel your distro is running.

```bash
make defconfig
make -j$(nproc)
```

Success looks like the build finishing with no error and producing `vmlinux` (and usually `arch/.../boot/bzImage` on x86). Failure is a hard stop in the log; scroll to the first `error:`.

If you only changed a single staging driver later, you can rebuild just that directory:

```bash
make -j$(nproc) M=drivers/staging/some_driver
```

You still do not need to install or reboot for a comment/typo patch. Do not skip the compile if you touched C.

---

### Step 3: Find a beginner-sized change

Do not start with networking core, MM, or a new driver.

**Good first targets**
- Typos / unclear sentences in `Documentation/` or in comments.
- Staging cleanups in `drivers/staging/`, especially items listed in that driver’s `TODO`.
- One warning that **your change** introduces zero new style problems.

**How to actually pick something**

```bash
find drivers/staging -name TODO
./scripts/checkpatch.pl --strict -f drivers/staging/some_driver/file.c
```

Then **search whether it is already fixed or already on the list**:

- `git log -p -- path/to/file` — maybe it was cleaned last week.
- [https://lore.kernel.org](https://lore.kernel.org) — search the filename or the exact typo.
- Do not send a “fix all checkpatch warnings in this 3,000-line file” bomb. One logical issue per patch.

**Things that look easy but are not**
- License-text / SPDX arguments.
- Mass renames across a whole driver with no other point.
- `checkpatch` drive-bys in mature trees (`fs/`, `mm/`, `net/`) — those maintainers often do not want style-only noise.
- Some staging areas (historically `drivers/staging/media/`) discourage checkpatch-only work; read that directory’s `TODO` first.

Match local style: kernel C uses **tabs** (not 4 spaces), `/* comments */` rather than `//`, and `snake_case`. When unsure, copy the file you are editing, not your userspace habits. Full rules: `Documentation/process/coding-style.rst`.

---

### Step 4: Change, commit, and write a kernel-style message

```bash
git checkout -b staging-foo-fix-typo
```

Edit **only** what the commit is about. Then stage specific files, not the whole tree:

```bash
git add path/to/the/file.c
git diff --cached          # read this; this is what reviewers see
git commit -s
```

`-s` appends `Signed-off-by: Your Real Name <you@example.com>`.

**Commit message shape (this is where most first patches fail)**

```
subsystem: short imperative summary

Explain the problem and why this change is correct.
Wrap the body at ~75 characters.

Signed-off-by: Your Real Name <you@example.com>
```

Rules beginners miss:
- First line: **subsystem prefix** + what the patch does, imperative (“fix”, not “fixed” / “fixes typo in file”).
- Example: `staging: foo: fix spelling of "controller" in comment`
- Example: `docs: submitting-patches: fix broken lore.kernel.org URL`
- Subject roughly **under 75 characters**, not a GitHub essay.
- Blank line between subject and body.
- Body explains **why**, not a repeat of the diff.
- Look at prior messages for that file: `git log --oneline path/to/file`.

`Signed-off-by` means you certify the [Developer’s Certificate of Origin](https://www.kernel.org/doc/html/latest/process/submitting-patches.html): you wrote this or have the right to submit it under the file’s license, and the contribution may appear in the public history. That is why the name must be real.

One commit = one logical change. A typo fix and a functional change are two patches.

---

### Step 5: Format, check, find recipients, send mail

**1. Make a patch file from the last commit**

```bash
git format-patch -1
```

You get something like `0001-staging-foo-fix-spelling-of-controller-in-comment.patch`.

**2. Run checkpatch on the patch, not only on the file**

```bash
./scripts/checkpatch.pl 0001-*.patch
```

Fix **errors**. Treat warnings as “justify or fix.” Do not “clean” unrelated lines just to silence the script; that inflates the diff.

**3. Read `get_maintainer.pl` output**

```bash
./scripts/get_maintainer.pl 0001-*.patch
```

Typical lines:

```
Some Maintainer <someone@example.com> (maintainer:FOO DRIVER)
linux-staging@lists.linux.dev (open list:STAGING)
linux-kernel@vger.kernel.org (open list)
```

- **To:** the listed maintainer(s) and the **subsystem list**.
- **Cc:** other reviewers the script names, and usually `linux-kernel@vger.kernel.org`.
- Do **not** send a first typo patch only to Linus. He is not the reviewer for staging or docs.
- Do not invent extra lists. Wrong list = ignored mail.

**4. Configure sending (do this once)**

Patches must be **plain text, inline in the email body**. Not an attachment. Not HTML. Gmail/Outlook web UI will wrap lines and destroy the patch. Use `git send-email` or `b4`.

Install is already done (`git-email`). Then point Git at your SMTP server. Example for a typical submission provider (values depend on your host; Gmail often needs an app password, not your login password):

```bash
git config --global sendemail.smtpserver smtp.example.com
git config --global sendemail.smtpserverport 587
git config --global sendemail.smtpencryption tls
git config --global sendemail.smtpuser you@example.com
```

Walkthrough many people use: [https://git-send-email.io](https://git-send-email.io). Client pitfalls: `Documentation/process/email-clients.rst`.

**5. Always dry-run, then send a copy to yourself**

```bash
git send-email --dry-run \
  --to="you@example.com" \
  0001-*.patch
```

If that looks right, send to yourself for real and confirm:
- subject starts with `[PATCH]`
- the diff is in the body, not attached
- lines are not wrapped in the middle of the diff
- `Signed-off-by` is present

Then send to the real recipients (paste addresses from `get_maintainer.pl`):

```bash
git send-email \
  --to="maintainer@example.com" \
  --cc="linux-staging@lists.linux.dev" \
  --cc="linux-kernel@vger.kernel.org" \
  0001-*.patch
```

**Using `b4` instead** (fewer SMTP foot-guns once configured):

```bash
b4 prep --auto-to-cc
b4 prep --check
b4 send --dry-run
b4 send --reflect          # copy to yourself first
b4 send
```

`b4` can also talk to kernel.org’s web submission endpoint if you set that up, which avoids fighting consumer SMTP. See [b4 documentation](https://b4.docs.kernel.org/).

---

### Step 6: After you send (the part the original guide skipped)

Public archives show up on [lore.kernel.org](https://lore.kernel.org). Search your subject or address. If it never appears, it bounced or landed in spam — fix SMTP before resending.

**Waiting:** a week of silence on a busy list is normal. Do not ping after two days. If nothing after ~two weeks, a short polite “just checking this was received” on the same thread is fine. Do not send a new identical thread without `RESEND` and a reason.

**Review replies**
- Reply **on the mailing list thread**, not a private side channel (unless the maintainer asks).
- Bottom-post / inline-reply. Do not top-post (“see my new patch below” above a quoted wall).
- Be brief and specific. “Fixed in v2” is enough when it is true.

**Sending v2** after you change the commit:

```bash
git add path/to/file.c
git commit --amend -s     # only if it has not been widely reviewed yet
# or make a new commit and squash while the series is still yours

git format-patch -1 --subject-prefix="PATCH v2"
```

In the mail, **below** the `---` line (not in the commit body that gets merged), add a short changelog:

```
---
v2: fix wording suggested by Jane Doe
```

Use `git send-email --in-reply-to='<message-id-of-v1>'` so v2 stays in the same lore thread.

**How you know it landed:** the maintainer applies it to their tree; later it appears in `git log` on linux-next and then in a Linus release. Nobody files a GitHub “merged” event. Watch lore, the maintainer’s git tree, and eventually [https://git.kernel.org](https://git.kernel.org).

---

### Contributor vs maintainer (realistic timeline)

- **Contributor:** you send patches. You also review other people’s patches on the list for the same files. Review is how people learn the subsystem.
- **Maintainer:** someone already trusted for a directory. They apply patches, run tests, and send pull requests to a higher maintainer or to Linus. That trust is months to years of consistent, correct work in **one** area — not a pile of random typos across the tree.

Practical path: pick one directory you care about, keep sending small real fixes, answer review, review others. Merge rights are given, not requested as a title.

---

### Beginner checklist before the first send

- [ ] Real `user.name` / `user.email`
- [ ] One logical change, specific `git add`
- [ ] Subject has subsystem prefix
- [ ] `git commit -s` and DCO line present
- [ ] `checkpatch.pl` on the `.patch` is clean enough to justify
- [ ] Recipients come from `get_maintainer.pl`
- [ ] Dry-run + mail to yourself; patch is inline plain text
- [ ] You searched lore so you are not duplicating a patch already in flight

