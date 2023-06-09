# QUESTIONS-
- What is socket and how does it helps in communication?
- What is index in linux?
- Why do we install packages as sudo user?
- What are environment variables and what are they used for?
- How you can verify that whether the installed package is official(real package) or a compromised package?
- How you can verify that the package installation is successful or not?
- What env. variables do you know?
- How env. variables helps our apllication to store sensitive data?
- How to verify the unset env variable is not available anymore?
- How does commands woke?
- How to create your own linux commands and environment variables?
- How to remove your own created linux command from the env?
- How OSI Model is implemented in linux?
- What are socket files?
- What is SSH protocol?
- What are ports?
- What is net cat command is used for?
- What is netstat -tuna command? What is -tuna flag stands for and why is it used?
- How to terminate the remote server?

# Practical:-
- Install docker on your machine.

# LEARNINGS FROM TODAY'S LECTURE-
- Group of virtual machines (called nodes in a network) that interacts with each other forms the cluster. Example - Kubernetes Cluster.
- Every application interacts/communicates with each other using linux sockets at the lowest level. Sockets allows the most basic communication among the devices.
- Package manager in linux is used to install packages.
- apt = Advanced Packaging Tool
- We can either use apt -get or apt only to work with our package manager.
- "sudo apt -get update" command is used to update the index in linux i.e. this command don't install anything on the limux system but provides the latest version of the packages.
- "sudo apt -get install <package-name>" command may even install the old version of the package. Thus, run "sudo -apt get update" everytime before installing a package.
- Installed packages goes to "archive" directory of our linux system.
- "/var/lib/apt/lists/" holds the list of all packages present in the archives (this location hods the package name, its meta-data, but not the data of the package as it is very heavy = this all information constitutes the index)
- /var stores application data like browser data, picture/image data etc.

- When we install git (using "sudo apt -get intall git"), Git creates its own archive for many reasons. It don't uses Ubuntu archive.
- We use sudo to run the commands related to package management because since on installation of package we update it's index thus making changes to /var/lib/apt/lists, which only root user has permission to make these changes.
- Other users have read-only permissions for /var/lib/apt/lists, thus they don't play a role in package management.
- Try to run apt -get without sudo -- it throws an error.
- "sudo apt -get install <package_name" command used to install a package on our system.
- "sudo apt -get install docker" -> install the docker on our linux system but it may even install a compromised Docker that looks and works same like official Docker but may steal the user data under the hood. Thus, we need to add Docker's official GPG key which verify the integrity of Docker installation.
- Docker maintains its own archive file.
- Environment variable are the system variables present in every processes. In linux, everything is either a file or a process. Terminal is itself a process.
- "echo $HOME" -- environment variable for "home". Purpose of home variable -- gives absolute path to home directory.
- "printenv" command prints all the environment variable present in the system.
- ".env file" -- sets all the variables as environment variable. It is not native to Ubuntu system.

- EXAMPLE: 
            - Let's consider a python application interacting with the database.
            - It requires a password to access the database and retrive the data from it.
            - Password is never stored in the code as the code may be publicably available on GitHub.
            - How environment variable can help in this case to allow our applications to store sensitive data? How env. variable hides our password from the readers?
            
 - PATH -> an important env. variable.
 - /bin directory holds the binary execuatables.
 - mkdir (and many other linux commands) is a binary executable file.
 - "which git" command shows where in the system git command is present
 - "which mkdir" command shows where in the system mkdir command is present. It is present in /bin/mkdir location i.e mkdir command binary executable is present in the /bin directory.
 - For every command in the bash, there is a binary execuatble file located somewhere in the system that gets executed when the command is executed.
 - "echo $PATH" command shows the various paths seperated by ":" as a seperator.
 - When $docker is executed on terminal, under the hood execuatble location is searched from PATH env variable.
 -  "unset PATH" command deletes the env variable 'PATH'.
 - We can verify that the unset environment variable exists no longer by executing the command "echo $name_of_unset_env_variable"
 - Some commands use PATH env. variable to woke but some doesn't.
 - Environment variables are transferred in form of inheritance. Parent process tranfers its env. variables to its child processes.
 - Use "export" command to create your own environment variable.

### OSI MODEL
 - Similar to Airline System where services at each layer trusts the data or services received fro  upper layer (At departure side) andserves the down layers.
 - Each layer uses the services offered by layers above it (At client side).
 
### LAYERS AVAILABLE
  1. Application layer - Used to make requests. More closer to the user.
  2. Transpoert layer - Segments the data. If any of the segment is not transmitted  properly, it is retransmitted by the TCP protocol used at this layer.
  3. Internet layer - IP protocol present at this layer. It takes 1śegment at a time and sends it over the internet b/w the source and the destination. This layer don't care about the content of each segment or whether it has been retranmitted or not.
  4. Network Interface layer - Very low level layer. Takes data as bits and converts it to EMI signals or other types of signal for transmission through different media like cables or through satellites.
  
  
  - In linux, OSI Model is implemented using the sockets.
  - Since everything in linux is a file, communication is also a file.
  - Create a socket file  to communicate. Designed to send data to receiver (e.g. sending data to google.com)
  - Writing data to soket file is similar to writing data to regular files. Kernel is responsible to send the data over the internet.
  - Server also contains socket files to communicate with the clients.
  - ssh protocol allows us to execute linux commands in remote server.
  
  
  - EXAMPLE:
            - we use "server.c" from the bootcamp repo to work with the remote server.
            - on terminal "$ssh ubuntu@public_ip_address_of_remote_server" command. Here 'ubuntu' is the username and 'public_ip' is the hostname.
            - on execution of the above command, error is thrown because we need credentials to prove that we have access to the server.
            - on terminal, execute "$ssh -i identity_of_the_user ubuntu@public_ip_of_remote_server".
            - on terminal, execute "chmod 400 identity_of_the_user". 400 -> wants reader to have only read permissions.
            - Now we can execute commands on the remote server using our local terminal of the terminal.
            
   - Port is a way to communicate with a process.
   - Combination of IP address and port allows us to communicate over a network.
   - "netcat" command is used to send data to the server. Command = "net cat public_ip_of_the_server port_number". Port number used is 9999.
   - "netstat" command investigates our current n/w connections.
   - "netstat -tuna" command lists all our currently present sockets. "-tuna" is similar to writing -t -u -n -a.
   - Server has a main socket on which it listens to the requests of the clients. Whenever we connect to a server, a new socket opens upb/w the user and the server.
   - Each connection is a seperate socket file.
  
  
  
 
 
            
