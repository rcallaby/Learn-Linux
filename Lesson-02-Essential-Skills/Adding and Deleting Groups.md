# Adding and Removing groups to Linux

# Managing Users and Groups in Linux



## Prerequisites

* You need to be the **root user** or have **sudo privileges**.
* Familiarity with basic Linux CLI is assumed.

---

## Understanding User and Group Files

Before modifying users and groups, you should understand where this data is stored:

* `/etc/passwd` — list of users
* `/etc/shadow` — user passwords (hashed)
* `/etc/group` — list of groups
* `/etc/gshadow` — group passwords (if used)

Always back up these files before doing large user/group operations.

---

## Adding a User

### Command: `useradd`

#### Basic Example

```bash
sudo useradd username
```

This creates the user, but it won’t set a password yet. You can’t log in as this user until you set one.

#### Full Example with Common Options

```bash
sudo useradd -m -s /bin/bash -c "Full Name" username
```

**Breakdown**:

* `-m` — create home directory `/home/username`
* `-s` — specify default shell (e.g., `/bin/bash`)
* `-c` — comment field (usually full name or description)

#### Setting the Password

```bash
sudo passwd username
```

This interactively sets the password (hashed in `/etc/shadow`).

---

## Adding a Group

### Command: `groupadd`

```bash
sudo groupadd groupname
```

You can also specify a group ID:

```bash
sudo groupadd -g 1234 groupname
```

---

## Adding User to a Group

### Command: `usermod`

To add an existing user to an **existing group**:

```bash
sudo usermod -aG groupname username
```

**Important**: always use `-aG` to avoid removing the user from existing groups.

---

## Deleting a User

### Command: `userdel`

```bash
sudo userdel username
```

If you also want to delete their home directory:

```bash
sudo userdel -r username
```

**Caution**: this deletes `/home/username` — back up important data first!

---

## Deleting a Group

### Command: `groupdel`

```bash
sudo groupdel groupname
```

**Note**: This does *not* delete users — it just removes the group entry from `/etc/group`.

---

## Checking User and Group Info

### List all users

```bash
cat /etc/passwd
```

Or view users with a home directory:

```bash
awk -F: '$3 >= 1000 {print $1}' /etc/passwd
```

*(On most distros, regular user IDs start at 1000)*

### List all groups

```bash
cat /etc/group
```

---

## Best Practices and Notes

* Always **set a password immediately** after adding a user.
* Avoid reusing **UIDs or GIDs** manually — let the system handle them unless you have a reason (such as syncing between servers).
* If you script user creation, test it first, and validate `/etc/passwd` and `/etc/group` after running.
* **Back up** `/etc/passwd`, `/etc/shadow`, `/etc/group`, `/etc/gshadow` before bulk changes.

---

## References

* `man useradd`
* `man userdel`
* `man groupadd`
* `man groupdel`
* `man usermod`
* Red Hat Enterprise Linux 9 docs: [https://access.redhat.com/documentation/en-us/red\_hat\_enterprise\_linux/9/](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/9/)
* Ubuntu Server Guide: [https://ubuntu.com/server/docs](https://ubuntu.com/server/docs)
* Linux System Administrator’s Guide — The Linux Documentation Project: [https://tldp.org/LDP/sag/html/](https://tldp.org/LDP/sag/html/)


