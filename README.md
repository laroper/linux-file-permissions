# Setting File Permissions in Linux
**Project Description:** Examine an existing permission of a file system and check if permissions matched the authorization that should be given. 
If they didn’t match, I needed to modify the permissions to the appropriate users and remove any unauthorized access.

### 1. Check file and directory details
  In the screenshot below I used the `pwd` command to show my current location in the directory,
  then navigated to the project folders. I then used the `ls -la` command to list all the files and hidden
  files in the directory choosing the files permission for each.
  
![1-File-Directory-details](https://github.com/laroper/linux-file-permissions/assets/165287449/3766b808-f7af-428a-a6f0-a6385224b55a)

### 2. Describe the permissions string
eg.1 ``` drwx--x--- 2 researcher2 research_team 4096 Jan 9 02:14 drafts ```

The example above shows the permissions string for the `drafts` subfolder. It contains a 10-character string that indicates how the permission on the
directory is set. 
+ In eg.1 above the 1<sup>st</sup> string with the `d` indicates that the file type is a directory.
+ The 2nd-4th characters indicate the read ( r ), write ( w ), and execute ( x ) permissions for the `user`.
+ The 5th-7th characters indicate the read ( r ), write ( w ), and execute ( x ) permissions for the `group`.
  You will realize the 5th and 6th character has a hyphen ( - ) instead of r or w, this indicates that this permission is not granted for the group.
+ The 8th-10th characters indicates the permission for the owner type called `other`. As you can see it only has hyphens
  which would indicate that the read, write, execute permission is not granted to other.

### 3. Change file permissions
Owner type `other` is not allowed to have write permission to any files. This was removed with the `chmod` command below.
``` 
chmod o-w project_k.txt
```

### 4. Change file permissions on a hidden file
The hidden file should not be written to by anyone, but should still be read by `user` and `group`. Hidden files are identified with a dot before the file name.
In the screenshot below the hidden file is made visible with the use of the `ls -la` command. I used the `chmod` command to set `user` and `group` to have only
read privileges and then removed all permissions from other. 

![2-file-perm-hiddenfile](https://github.com/laroper/linux-file-permissions/assets/165287449/35dfe952-394b-4e67-81ea-e61f5490272e)

The example above shows the hidden file `.project_x.txt` having the following permission set ``` chmod u=r,g=r,o-rw .project_x.txt ```:
+ Owner type `user` getting read access  `u=r`
+ Owner type `group` getting read access - `g=r`
+ Owner type `other` loosing read and write access - `o-rw`
  
### 5. Change directory permissions
The only the researcher2 user was allowed access to draft directory and its content -meaning only `user` should have execute privileges

In the screenshot below I used the `chmod` command to set all permission for `user`, removed all permission for `group` and `other`. Then the `ls -la` command to
display the change on permissions.

![3-change-directory-perm](https://github.com/laroper/linux-file-permissions/assets/165287449/dd294294-c2d2-40f4-8356-e31eada6654b)

### Summary
This project was to show my ability to navigate the linux file system, to list directory files for subfolders and hidden files. It also show my ability to
make changes to file permissions for directories, files and hidden files.
