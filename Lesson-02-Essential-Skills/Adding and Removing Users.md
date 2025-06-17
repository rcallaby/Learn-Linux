# Adding and Deleting Users to Linux

## Key Files to Know

Before working with users, understand where Linux stores this data:

* `/etc/passwd` — user account details (UID, home, shell, etc.)
* `/etc/shadow` — hashed passwords and password aging info
* `/etc/group` — primary and secondary groups
* `/etc/gshadow` — group password and administration info

Backup these files with `cp` before mass changes:

```bash
sudo cp /etc/passwd /etc/passwd.bak
sudo cp /etc/shadow /etc/shadow.bak
sudo cp /etc/group /etc/group.bak
sudo cp /etc/gshadow /etc/gshadow.bak
```

---

## Adding a User

### The Basic Command

```bash
sudo useradd username
```

This creates a user **without setting a password** — they will not be able to log in until you set one.

---

### Recommended Full Command

```bash
sudo useradd -m -c "Full Name" -s /bin/bash username
```

**Options**:

* `-m` — Create the home directory `/home/username`
* `-c` — Comment (Full Name or Description)
* `-s` — Login shell (default is often `/bin/bash`)

---

### Setting the User Password

After creating the user, immediately set their password:

```bash
sudo passwd username
```

The system will prompt for the new password twice. The hash is stored in `/etc/shadow`.

---

### Setting UID or GID Manually (Advanced)

In some environments (NFS shares, LDAP), you might want to manually specify UID or GID:

```bash
sudo useradd -u 1500 -g 1000 -m -s /bin/bash username
```

* `-u` — set user ID (UID)
* `-g` — set primary group ID (GID)

---

## Viewing User Details

You can view the user in `/etc/passwd`:

```bash
grep username /etc/passwd
```

Example output:

```text
username:x:1500:1000:Full Name:/home/username:/bin/bash
```

Fields:

1. username
2. x (password field placeholder, actual hash is in `/etc/shadow`)
3. UID
4. GID (primary group)
5. Full name/comment
6. Home directory
7. Shell

---

## Deleting a User

### Command: `userdel`

To delete a user **without deleting their home directory**:

```bash
sudo userdel username
```

---

### Delete User and Home Directory

To remove the user *and* their home directory `/home/username`:

```bash
sudo userdel -r username
```

**Caution**: This also removes user-owned files in `/home/username` — back up important data first.

---

## Verifying User Deletion

After deleting a user, check `/etc/passwd` to ensure the account is gone:

```bash
grep username /etc/passwd
```

If there is no output, the user is removed.

Also check the home directory:

```bash
ls -l /home/username
```

If using `-r`, this directory should be gone.

---

## Best Practices for Adding and Deleting Users

* Always set a password immediately after creating the user.
* Use `-m` to ensure a proper home directory is created.
* Do not delete a user until confirming no important files remain.
* Use backups before mass deletion.
* Use `usermod -L username` to lock accounts if you need to suspend instead of delete.
* For auditing, always log user addition and deletion in `/var/log/secure` (RHEL) or `/var/log/auth.log` (Ubuntu/Debian).

---

## References

* `man useradd`
* `man userdel`
* `man passwd`
* Red Hat Enterprise Linux 9 docs: [https://access.redhat.com/documentation/en-us/red\_hat\_enterprise\_linux/9/](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/9/)
* Ubuntu Server Guide: [https://ubuntu.com/server/docs](https://ubuntu.com/server/docs)
* The Linux System Administrator’s Guide — The Linux Documentation Project: [https://tldp.org/LDP/sag/html/](https://tldp.org/LDP/sag/html/)
