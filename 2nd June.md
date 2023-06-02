## IMPORTANT QUESTIONS
- what is the use of sudo command?
- why is sudo command used for installing packages.


## IMPORTANT POINTS
- in /proc  ; use 'cat cpuinfo' to have cpu related info.
- use 'cat meminfo' to know about memory usage and 'free -h' to obtain current RAM usage and swap space.
- to determine the currently loaded drivers use 'lsmod' which gives info about module name, size, dependencies.
- use 'uptime'to know for how long the linux system has been running.
- use 'cat /proc/filesystems' to know about the filesystems known by our system.
- 


- if filename starts with (.) it is hidden; files with different permissions sets are usually hidden a bit more hidden permissions.
- in linux you can't tell simply by looking if it is file or directory.
- wildcards are similar to regex; allows you to list file directories and files according to a pattern.
- '.*' (.) is for every word or frame and (*) is for every everything.
- use 'ls b*' to list files starting with b and * for everything.
- by 'umask' we can see the default permissions of a file. 
- 'ls -l filename' can also be used to check the permissions of a file.
- in linux every command like pwd is abbreviation.
- sudo is 'switch user and do'
- sometimes you have to execute commands on behalf of other users; so to save time to switch the user to another and come back we use sudo. it allows you to execute commands ad root user.
- 
