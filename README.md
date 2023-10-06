# File-permissions-in-Linux

The security team was tasked with updating permissions for the files and directories within the `project’s` directory for our company’s research team. To keep the system secure, these steps were taken:

## Check file and directory details

Command `ls -la` in the projects directory was used. This command gives a detailed list of all contents within the project's directory, including hidden files. There is a 10-character string in front of all the files listed that displays the permissions for each directory within the project's directory. These show that the permissions are not set correctly and need to be updated.

## Describe the permissions string

The permissions string is a 10-character string that determines who is authorized to access the file and their permissions.

- The 1st character tells you what type of file it is. A `d` means it’s a directory while `-` means it’s a regular file.
- The 2nd-4th characters tell you the permissions set for the user. The permissions are indicated by different characters as follows: `read (r)`, `write (w)`, and `execute (x)` if one of these is a `-`, then that means that permission was not granted.
- The 5th-7th characters show permissions (`r`, `w`, `x`) for the group. A hyphen indicates no permission given.
- The 8th – 10th characters show the permissions for others, who are anyone other than the user and group.

For example, `project_m.txt` reads as a regular file because it starts with a `-` hyphen. Then the next three characters are `rw-`, which means the user has permission to read and write but not to execute the file. The following three characters after that first set are for the group permissions. Those characters show they have permission to read but not write or execute the file, looks like this: `r--`. Lastly, the three characters at the end are for others. They don’t have any permissions for this file, which is demonstrated by all three characters being hyphens `---`.

## Change file permissions

The company stated they didn’t want others to have write access to any of their files. Checking the previously returned file permissions, I could see that `project_k.txt` needed to have the write permission removed. I did this by typing in the command `chmod o-w project_k.txt` and hitting enter. The `chmod` command is to change permissions on files and directories. The first argument shows what permissions need to be changed, and the second argument shows which file or directory to change. I then typed in `ls -la` to double-check that the changes were made and that no other files needed to be updated.

## Change file permissions on a hidden file

The research department had just archived `project_x.txt`. They said they don’t want anyone to have write access to this project, but the user and group should be able to read it. I used the following command to achieve this: `chmod u-w, g-w, g+r .project_x.txt`. By using this command, I was able to remove write permissions for both the user and group, represented in the command like this `u-w, g-w`, and add reading permissions to the group, represented in the command like this `g+r`.

## Change directory permissions

The company said they only want the `researcher2` user to have access to the `drafts` directory and its contents. No one else is to have access to this directory. To do this, I used the command: `chmod g-x drafts`. The group needed the execute permissions removed while the user already had access to the directory, so no changes were needed for the user or others because others had no permissions to begin with.

## Summary

I used Linux commands to make multiple changes to files and directories in the projects directory to meet my company’s needs. The first step was using the command `ls -la` to check for the existing permissions for the directory. This showed me what changes needed to be made and to which files. Then I used the `chmod` command to execute those changes to permissions on the files and directories.
