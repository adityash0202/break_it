The secure encrypted file system will be integrated into the host file system just like a standard file system, but it offers enhanced security measures. It serves multiple clients or users to efficiently utilize available storage space, eliminating the need for separate storage for each user.

### COMPILE

```
git clone <repo>
cd <repo>
docker build .
docker images 
```

run the latest image being created with the following command 

```
docker run -it <image sha256> /bin/bash
```


### User Functionalities
* cd <directory> - Allows users to switch to a specified directory. It accepts . and .. as references to the current and parent directories, respectively. It supports changing to multiple directories simultaneously (e.g., cd ../../dir1/dir2). Typing cd / takes you to your root directory. If the specified directory doesn't exist, you remain in the current directory.
* pwd - Displays the current directory path. Users have base directories at /personal and /shared.
* ls - Lists the files and directories in the current directory, displaying them on separate lines. It also shows the special directories . and ... To distinguish between files and directories, the output format is as follows:
 ```
 d -> .
 d -> ..
 d -> directory1
 f -> file1
```
* cat <filename> - Reads the decrypted contents of the specified file. If the file doesn't exist, it prints "<filename> doesn't exist."
* share <filename> <username> - Shares the file with the specified target user, making it accessible in the /shared directory of the target user. The file is shared with read-only permission. The shared directory is also read-only. If the file doesn't exist, it prints "File <filename> doesn't exist." If the target user doesn't exist, it prints "User <username> doesn't exist."
* mkdir <directory_name> - Creates a new directory. If a directory with the same name already exists, it prints "Directory already exists."
* mkfile <filename> <contents> - Creates a new file with the provided contents, which should consist of printable ASCII characters. If a file with the same name exists, it replaces the contents. If the file was previously shared, the target user will see the updated contents of the file.
* exit - Terminates the program.



### Admin Functionalities
The admin has full access to the entire file system and can perform all user functions.
`adduser <username>` - This command generates a keyfile named username_keyfile on the host, which is used by the user to access the file system. 
If a user with the same name already exists, it prints "User <username> already exists."
