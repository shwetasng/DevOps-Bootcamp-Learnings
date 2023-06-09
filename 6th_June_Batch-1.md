## QUESTIONS
- How we can maintain the HTTP Backend?
- Why do we need a virtual environment if we can run the code locally on our machine?

## PRACTICAL
- Using app.py from the bootcamp repo, create a virtual environment and install the flask package.

## LEARNINGS FROM THE CLASS
- Socket is the lowest level interface to communicate over the network. Socket is like a regular file from which we can read and write the content to it.
- In server.c file (present in DevOps bootcamp repo), there are 3 system calls:- 
   1. socket() -- creates a socket file
   2. bind() -- makes socket communicable
   3. listen() -- we start listening through port number.
   
- ## SUBNETS
  - Apllications are not deployed on a single server becuase it increses the risk of single point of failure, rather the apllications are deployed in clusters which is set of independent machines reducing the chances of single point of failure.
  - Example: We experience github.com as a single service but under the hood it is composed of many microservices. This architecture is called miceroservices.
  - All the microservices runs on close serves so as to reduce the latency i.e. microservicesare made available within the same network. Hence, we need to learn about subnets so as to make all the microservices related to a single service available within a single network.
  - Read about Route Table, Network Interface and Default gateway.
  - 3 important protocols: HTTP, DNS, SSH
  
- ## DNS
  - Allow to convert the domain name to its corresponding IP address.
  - Computers dont know what to do with the hostname. They rely on IP address to communicate with each other over the network.
  - Humans don't learns the IP address as it keeps on changing.
  - DNS Protocol is a function whose input is the DNS name and output is the corresponding IP address.
  - Command to resolve DNS name = 'nslookup"
    Example: "$nslookup google.com"
  - Idea of using a single DNS server to get the IP address (mapping of DNS name to IP Address) is not a good idea because of the following reasons:
            - Single point of failure.
            - Heavy traffic on a single server.
            - Inefficient resolution of the DNS name
            - Centralization
            - Maintenence
  - Example:
            - We want to resolve google.cm
            - First we go to the ROOT SERVER by using the IP address of the root server provided by our ISP. Once the IP address of the root aervers are fetched,               they are cached to our machine for future use.
            - The request to resolve the DNS name is sent to one of the root server among all the available server.
            - Root server redirects the request to the group of servers responsible for (.com) domain aclled TOP LEVEL DOMAIN SERVER. Request reaches to (.com)                 server.
            - Top level domain server don't know the IP address of google.com thus, it redirects request to AUTHORITATIVE SERVER. It provides the corresponding IP               address of the provided DNS name.
           
  - Hierarchy of servers for DNS name resolution :- 
                            ROOT SERVER ->  TOP-LEVEL DOMAIN SERVER ->  AUTHORITATIVE SERVER
  - First 2 levels of the hierarchy are just to redirect the request to the appropriate authoritative server, thus removing the limitations associated with the       design of single server for DNS resolution.
  - User don't need to take care of the maintenance of the authoritative server to maintain their domain. Can be maintained using paid services like Amazon Web       Services or Go Daddy
  
  - "dig command" can be used as an alternate to the "nslookup" command--- Output generted using dig command is more clear.
  
  - EXAMPLE: Using "dig" command to resolve google.com through the hierarchy of available servers.
               - "$dig . NS " command to list down all the root level servers. This command is used to resolve the root level server of google.com. "." is used to                   ask about the root level domain.
               - We need to choose any one of the root server obtained from above executed command.
               - "$dig @ name_of_selected_root_server .com NS" command is executed to get the details of all servers storing .com domain (top-level server).
               - Select one of the .com server from above executed command to know the address of google.com
               - "dig @ name_of_.com_server NS" command to know the address of google.com (authoritative server).
               - Select one of the authoritative server obtained from above command to know the IP address of 'google.com'. We don't use NS record rather uses A                    record because we are already at the leaf level and don't require the information about the next level servers.
 
 - In all the steps executed above we are travelling down the hierarchy of servers to resolve the DNS name.
 - Maintaining this kind of hierarchy is helpful for traffic distribution, reduces single point of failure and is robust.
 - But traversing the entire hierarchy everytime may not be efficient and can be time-consuming. The solution to this problem is done by caching the IP addresses    using local DNS Server maintained by the ISP .
 - EXAMPLE: On repeated execution of the command "dig google.com" results in TTL=0 (because the IP address is cached in the local DNS server for the time it is               valid). Once the time after which the cached IP address becomes invalid, entire process is repeated again( from root server to authoritative srever).
 
 ## HTTP Protocol
 - Textual protocol. Text in HTML. Browser knows how to run this text in visual way.
 - Widely used on internet.
 - HTTP request and HTTP response.
 - "curl -v http://httpbin.org/html" command is used for HTTP Request and HTTP Response.
 - curl is used to invoke HTTP request and getting back the response in textual format.
 - http://httpbin.org/html is the dummy server.
 - HTTP Response contains the status code (like connection:keep-alive --> i.e. the socket connection is kept alive to allow communication corresponding to future    requests easily).
 - GET & POST REQUEST, DELETE REQUEST
 - We can ask to keep the socket connection alive for a specific period of time.
 
 - How we can maintain HTTP server (maintaining the backend)?
 - We create virtual environment to keep the develpoment process isolated and for easier debugging. Different applications may require different environment for its execution (we cannot set diff env for each application), thus, we use virtaul environment. Anything that break in the virtual environment does not disturb the local environment of our machine.
 - There are two ways to communicate with the servers :- UI and API(used when one apllication wants to communicate with another application).
 - " curl -x POST -F 'file=@local-path-to-image-file' > localhost: 8080/api/upload" command used to upload a file to a server (using POST request).
 
                                  
                          
                              
