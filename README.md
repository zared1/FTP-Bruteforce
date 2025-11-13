# FTP Bruteforce

A minimal Python script that attempts to brute-force FTP logins by trying passwords from a newline-separated wordlist. Designed for lab/educational use only — **do not** run this against systems you don’t own or have explicit permission to test.

## Features

* Uses Python’s standard `ftplib` to connect to an FTP server.
* Reads passwords from a simple text file (one password per line).
* Attempts to log in with each password and prints the directory listing on success.
* Single-file, zero external dependencies (uses Python standard library).

## How to Run

1. Clone or save `FTP-bruteforce.py`.
2. Run the script:

```bash
python3 FTP-bruteforce.py <FTP_server_IP_or_hostname> <username> <passwords-file>
# Example:
python3 FTP-bruteforce.py 10.10.11.22 administrator ./passwords.txt
```

3. The script will attempt each password in the list. On successful login it prints the result of `ftp.nlst()` (directory listing) and the recovered password.

## Notes

* This script uses plain FTP (no TLS) and default FTP port. If the target uses a non-default port or FTPS you’ll need to adapt the code.
* The password file should be a newline-separated list. Empty lines are treated as attempts (you may want to pre-clean your wordlist).
* Add a timeout, delay, or rate limiting for large lists to avoid flooding the target.
* **Ethics & legality:** Only run this against systems you own or have explicit written permission to test. Unauthorized brute-forcing of services is illegal and unethical. Use this tool only for learning, CTFs, or authorized security assessments.
* For reliable remote administration and secure file transfers, prefer authenticated, encrypted protocols like **SFTP/SSH** or FTPS.

## Suggested improvements (optional)

* Add per-attempt timeouts and a small delay (`time.sleep`) between attempts.
* Support non-default ports and passive/active modes.
* Skip empty lines and log attempts to a file.
* Add thread-based or asynchronous attempts for speed (careful — increases noise).
* Support FTPS (secure FTP) or SFTP (use `paramiko`) for realistic testing of secure services.
