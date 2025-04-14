# SCP (Secure Copy Protocol) 

SCP is a widely used method to securely transfer files between computers over a network using SSH. 

1.	Copy a file from your local machine to a remote machine:

```bash
scp [options] source_file username@destination_host:destination_path
```

2.	Copy a file from a remote machine to your local machine:
```bash
scp username@remote_host:/path/to/remote/file /path/to/local/destination/
```

3.	Copy an entire directory (use -r for recursion):
```bash
scp -r /path/to/local/directory username@remote_host:/path/to/remote/destination/
```


## Options

1.	-r
Recursively copy entire directories.


2.	-p
Preserve file attributes such as modification times, access times, and modes.

3.	-q
Suppress non-error messages (quiet mode).

4.	-v
Enable verbose mode to see detailed output. Useful for debugging.

5.	-C
Enable compression during transfer to reduce file size (can speed up transfers on slower connections).

6.	-P <port>
Specify the port to connect to on the remote host (useful if the SSH server uses a port other than the default 22).

7.	-l <limit>
Limit the bandwidth for file transfer in kilobits per second (e.g., -l 500 limits to 500 Kbps).

8.	-4
Use IPv4 only for the connection.

9.	-6
Use IPv6 only for the connection.

10.	-o <SSH option>
Pass specific SSH configuration options (e.g., -o StrictHostKeyChecking=no).

11.	-i <identity_file>
Specify a private key file for authentication (useful if you’re using an SSH key instead of a password).

12.	-S <program>
Specify an alternative program for SSH (rarely used).
