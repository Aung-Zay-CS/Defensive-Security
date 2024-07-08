Linux systems provide a reliable and robust alternative to closed-source systems, such as MS Windows Server and UNIX.
Of course, we cannot claim that Linux is always the best choice; however, Linux is the best choice for many scenarios. Before using this option, we must focus on securing our Linux systems, also known as Linux hardening.

##  Physical Security
One of the security principles is Defence-in-Depth. Hence, we should always think in terms of layers of security. One of the first layers is physical security.
Let’s say you have taken the necessary measures to prevent intruders from taking the disk drive or the whole computer system.
Moreover, you have ensured that your system passwords are complex and impossible to guess.
If an intruder can access the system physically, it is a non-sophisticated task to use GRUB, a popular Linux bootloader, to reset the root password account.
Hence we have the adage “boot access = root access”.

It is evident that we need to ensure physical security for our computer systems; however, in the unlikely event that physical security is breached, we need to provide additional layers of protection.
Many BIOS and UEFI firmware allows you to add a boot password. This password will prevent unauthorised users from booting the system.
However, this can only be used for personal systems; it won’t make sense to use it on servers as this will require someone to be physically present to supply the boot password.

We can consider adding a GRUB password depending on the Linux system we want to protect. Many tools help achieve that.
One tool is grub2-mkpasswd-pbkdf2, which prompts you to input your password twice and generates a hash for you.
The resulting hash should be added to the appropriate configuration file depending on the Linux distribution (examples: Fedora and Ubuntu).
This configuration would prevent unauthorised users from resetting your root password.
It will require the user to supply a password to access advanced boot configurations via GRUB, including logging in with root access.

###  grub2-mkpasswd-pbkdf2
Password-Based Key Derivation Function 2 (grub2-mkpasswd-pbkdf2) is a command-line tool used in Linux systems, particularly with GRUB 2 (Grand Unified Bootloader version 2), which is the bootloader used by most Linux distributions.

Its primary purpose is to generate hashed passwords using the PBKDF2 (Password-Based Key Derivation Function 2) algorithm.
This tool is typically used to secure GRUB bootloader configurations by encrypting passwords stored in configuration files (like /etc/grub.d/00_header or /boot/grub/grub.cfg). 
Which can help prevent unauthorized access or modification of bootloader settings.

Here’s a brief overview of how grub2-mkpasswd-pbkdf2 works:
- Generate a hashed password: When you run grub2-mkpasswd-pbkdf2, you provide it with a plaintext password. It then uses the PBKDF2 algorithm to generate a hashed representation of this password.
- Store hashed password: The hashed password can be copied and pasted into the GRUB configuration file (like grub.cfg). This hashed password is stored securely and can be used by GRUB during boot to authenticate users who need to access GRUB commands or change boot options.
- Security: Using PBKDF2 ensures that even if an attacker gains access to the configuration file, they won't immediately see the plaintext password. PBKDF2 is designed to be computationally intensive, making brute-force attacks on the hashed password more difficult.
- Usage: After generating the hashed password, you typically need to edit the GRUB configuration file (/boot/grub/grub.cfg) to specify where and how GRUB should use this password for authentication.

```
$ grub2-mkpasswd-pbkdf2
Enter password:
Reenter password:
PBKDF2 hash of your password is grub.pbkdf2.sha512.10000.[hash]
```
