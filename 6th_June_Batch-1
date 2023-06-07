- Socket is the lowest level interface to communicate over the network. Socket is like a regular file from which we can read and write the content to it.
- In server.c file (present in DevOps bootcamp repo), there are 3 system calls:- 
   1. socket() -- creates a socket file
   2. bind() -- makes socket communicable
   3. listen() -- we start listening through port number.
   
  - SUBNETS
  - Apllications are not deployed on a single server becuase it increses the risk of single point of failure, rather the apllications are deployed in clusters which is set of independent machines reducing the chances of single point of failure.
  - Example: We experience github.com as a single service but under the hood it is composed of many microservices. This architecture is called miceroservices.
  - All the microservices runs on close serves so as to reduce the latency i.e. microservicesare made available within the same network. Hence, we need to learn about subnets so as to make all the microservices related to a single service available within a single network.
  - Read about Route Table, Network Interface and Default gateway.
  - 3 important protocols: HTTP, DNS, SSH
  
  - DNS
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
            - First we go to the ROOT SERVER by using the IP address of the root server provided by our ISP. Once the IP address of the root aervers are fetched, they are cached to our machine for future use.
            - The request to resolve the DNS name is sent to one of the root server among all the available server.
            - Root server redirects the request to the group of servers responsible for (.com) domain aclled TOP LEVEL DOMAIN SERVER. Request reaches to (.com) server.
            - Top level domain server don't know the IP address of google.com thus, it redirects request to AUTHORITATIVE SERVER. It provides the corresponding IP address of the provided DNS name.
           
  - Hierarchy of servers for DNS name resolution :- 
                            ROOT SERVER ->  TOP-LEVEL DOMAIN SERVER ->  AUTHORITATIVE SERVER
  - First 2 levels of the hierarchy are just to redirect the request to the appropriate authoritative server, thus removing the limitations associated with the design of single server for DNS resolution.
  - User don't need to take care of the maintenance of the authoritative server to maintain their domain. Can be maintained using paid services like Amazon Web Services or Go Daddy
  
  - "dig command" can be used as an alternate to the "nslookup" command--- Output generted using dig command is more clear.
  
  -Example: Using "dig" command to resolve google.com through the hierarchy of available servers.
               - "$dig . NS " command to list down all the roo level servers. This command is used to resolve the root level server of google.com 
                                  
                          
                              
