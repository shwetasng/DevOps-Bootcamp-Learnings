## IMPORTANT QUESTIONS
- what is the use of sudo command?
- why is sudo command used for installing packages.
- what is the exit code ?
- checkout the real implementation of soft links and hard links.
- how do we know if a process requires CPU anymore or not?
- what are utility commands?
- Use of kill signal in linux?
- 


## IMPORTANT POINTS
### Exercise of Linux_intro
- In /proc  ; use 'cat cpuinfo' to have cpu related info.
- use 'cat meminfo' to know about memory usage and 'free -h' to obtain current RAM usage and swap space.
- to determine the currently loaded drivers use 'lsmod' which gives info about module name, size, dependencies.
- use 'uptime'to know for how long the linux system has been running.
- use 'cat /proc/filesystems' to know about the filesystems known by our system.


### discussed points in Class:
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
- difference between 'echo "hi" > filename' and 'echo "hi" >> filename' ; basically > is used to overwrite and >> for appending.
- google drive began with the idea of hard links.
- 

## LINKS IN LINUX
- in linux we can have 2 different files pointing to same inode.
- we created file named test and test2 and use " ln test test2 " to create a hard link it failed to create hard link. why? check what is the root cause of the problem.
- after 'rm test2' that is removing test2 we create a link again using 'ln test test2' now a hard link is created.
- in hard links both files will have same content but in windows we have soft links that are shortcuts.

## LINUX PROCESSES
- Kernel decides which pocess will come to CPU first; other processes are kept in queue.
- i/o operations take a lot of time so the process don't use CPU at that time.
- if we browse github and press enter; does this process requires CPU at this time? this is a http request means via ISP delhi ocean singapore github server then the response will be sent back. this process doesn't require CPU in the mean time since it is only waiting for reply github server hence it will go to waiting state.
- it is very rare to find process in zombie state it only stays there for nanp second and goes to terminate state.
- Linux divides your CPU in 10,000 milli CPU and a process can use for example 10 milli CPU; this is done to limit the CPU utilization by different processes.
- we use 'top' command to show running processes in real time.
- use 'ps' command to display information about processes.
- use ' sudo systemctl enable <service name> ' to enable a service to start automatically at boot time; here systemctl command is used to manage services in your system.
- under the hood 'ls' is a new process who has the parent terminal; use 'pstree' command to check this and you will see all the processes running.
- processes communicate with each other through signals.
  
