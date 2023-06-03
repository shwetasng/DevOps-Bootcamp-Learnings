## IMPORTANT QUESTIONS
- what is the use of sudo command?
- why is sudo command used for installing packages.
- what is the exit code ?
- checkout the real implementation of soft links and hard links.
- how do we know if a process requires CPU anymore or not?
- When and why does a process doesn't needs CPU anymore?
- what are utility commands?
- What are signals in linux and whey are they used?
- Use of kill signal in linux?
- How do we check that an object is whether a directory or a file?
- What are wildcards?


## IMPORTANT POINTS
### Exercise of Linux_intro
- In /proc  ; use 'cat cpuinfo' to have cpu related info.
- use 'cat meminfo' to know about memory usage and 'free -h' to obtain current RAM usage and swap space.
- to determine the currently loaded drivers use 'lsmod' which gives info about module name, size, dependencies.
- use 'uptime'to know for how long the linux system has been running.
- use 'cat /proc/filesystems' to know about the filesystems known by our system.


### discussed points in Class:
- if filename starts with (.) it is hidden; files with different permissions sets are usually hidden (a bit more hidden permissions).
- in linux you can't tell simply by looking at an object that if it is file or directory.
- wildcards are similar to regex; allows you to list file directories and files according to a pattern.
- '.*' (.) is for every word or frame and (*) is for everything.
- use 'ls b*' to list files or directories starting with b and * for everything.
- by 'umask' we can see the default permissions of a file. 
- 'ls -l filename' can also be used to check the permissions of a file.
- in linux every command like pwd is abbreviation.
- sudo is 'switch user and do'
- sometimes you have to execute commands on behalf of other users; so to save time to switch the user to another and come back we use sudo. it allows you to execute commands as root user.
- It's dangrepos to make changes as root user into the system. Hence, use root account wisely.
- difference between 'echo "hi" > filename' and 'echo "hi" >> filename' (REDIRECTION OPERATOR); basically > is used to overwrite and >> for appending.
- google drive began with the idea of hard links.
- 

## LINKS IN LINUX
- 2 types of links in Linux system : HardLink & Soft Link
- Soft Link : Similar to shortcut in Windows.
- Hard Link : Two files (may be present in different partitions of the disk) points to same inode (pointing to same area of memory in the disk). Changes made in one of the file will be reflected in the another file.
- in linux we can have 2 different files pointing to same inode.
- we created file named test and test2 and use " ln test test2 " to create a hard link it failed to create hard link. Why? check what is the root cause of the problem.
- after 'rm test2' that is removing test2 we create a link again using 'ln test test2' now a hard link is created.
- in hard links both files will have same content but in windows we have soft links that are shortcuts.

## LINUX PROCESSES
- Process is the set of instructions to CPU.
- Schedular decides which process to run.
- Kernel decides which process will come to CPU first; other processes are kept in queue.
- i/o operations take a lot of time so the process don't use CPU at that time. Process is in waiting state.
- if we browse github and press enter; does this process requires CPU at this time? This is a http request means via ISP delhi -> cables in ocean -> singapore github server, then the response will be sent back suing same mechanism. This process doesn't require CPU in the mean time since it is only waiting for reply from github server hence it will go to waiting state.
- use 'ping github.com' to know the time it takes for a request to reach the github server and response from server back to the client.
- it is very rare to find process in zombie state it only stays there for nano second and goes to terminate state.
- Process has a owner(similar to files).
- We can mimic the processes.
- Linux divides your CPU in 10,000 milli CPU and a process can use. For example 10 milli CPU (this means process uses CPU for 10msec and then leave the CPU for another process to use); this is done to limit the CPU utilization by different processes.
- we use 'top' command to show running processes in real time.
- use 'ps' command to display information about processes.
- use ' sudo systemctl enable <service name> ' to enable a service to start automatically at boot time; here systemctl command is used to manage services in your system.
- under the hood 'ls' is a new process who has the parent terminal; use 'pstree' command to check this and you will see all the processes running.(Parent-child processes)
- processes communicate with each other through SIGNALS.
  
## GRACEFUL TERMINATION
  - Graceful termination means that the process should complete the services it's offering to the user and then should stop accepting more requests of the      services. It should also release the resources it holds before its termination.
  - 'kill -l' gives list of all signals allowed with kill command.
  
  
- command 'kill -9 PID' kills a process forcefully leading to immediate termination.
- SIGTERM is a signal to ask the process to kill iteself (prior notification) & terminte gracefully.
- SIGKILL is a signal to kill the process forcefully.
  
- If users have old version running and new version has been launched then how do users switch to new version? Traffic is routed from old version to new version and the old version is terminted gracefully. This all ensures that the downtime is 0. 
- how to close process gracefully?
  in python we use (kill -9) to end process.
  - in graceful termination process server is closed for new requests so that it can start with its termination.
  - If the server holds some resources(like database) to serve the client's request, it needs to release and disconnect with those resources before server is closed so that the resources(like database) serving the database don't need to spend its resources further.
