- First launch an instance with your required specifications and either use your previous key-pair of create a new one and download it.
<img width="770" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/85c69211-5236-4f00-bc4a-816743529597">

- Connect to your server from your systems terminal using ssh command as shown:
<img width="565" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/1a69037a-8ba6-45ab-b0a9-a8eefd5c12a1">

- if you face permission denied error due to permission set of your private key then using chmod 400 command set the permissions for your .pem file which is your key and you are good to go.
- You will be connected to your server like this:
<img width="502" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/49a7d541-edd5-4e2d-8bd5-1ab281e4e36b">

- we then made a file named server.c in our ubuntu-aws server and copied the below code in it.
```text
// compile by `gcc -o server server.c`

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <strings.h>
#include <sys/socket.h>
#include <resolv.h>
#include <arpa/inet.h>
#include <errno.h>

#define MY_PORT		9999
#define MAX_BUF		1024

int main()
{
    int sockfd;
	struct sockaddr_in self;
	char buffer[MAX_BUF];

    // To create a socket for networking communication. A new socket by itself is not particularly useful
    sockfd = socket(AF_INET, SOCK_STREAM, 0);

	/** Initialize address/port structure */
	bzero(&self, sizeof(self));
	self.sin_family = AF_INET;
	self.sin_port = htons(MY_PORT);
	self.sin_addr.s_addr = INADDR_ANY;

    // The bind call associates an abstract socket with an actual network interface and port
    bind(sockfd, (struct sockaddr*)&self, sizeof(self));

    // The listen call specifies the queue size for the number of incoming, unhandled connections
	listen(sockfd, 40);

	/** Server run continuously */
	while (1)
	{	int clientfd;
		struct sockaddr_in client_addr;
		int addrlen=sizeof(client_addr);

		/** accept an incomming connection  */
		clientfd = accept(sockfd, (struct sockaddr*)&client_addr, &addrlen);
		printf("%s:%d connected\n", inet_ntoa(client_addr.sin_addr), ntohs(client_addr.sin_port));

		/** print the received data to the client */
		int read_bytes = read(clientfd, buffer, MAX_BUF);
		printf("Got client message: %s\n", buffer);
		write(clientfd, buffer, read_bytes);

		/** Close data connection */
		close(clientfd);
	}

	/** Clean up */
	close(sockfd);
	return 0;
}
```
- and using command: "gcc -o server server.c" we compiled the code. we can se the output, source code is in server.c and server has the executable code:
<img width="295" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/510aec32-e8af-4376-9bd7-40ed4fbe21c2">

- when we go through the code we get to know that our server is listening to post:9999 and command: "sockfd = socket(AF_INET, SOCK_STREAM, 0);" is used to create a socket. First time we create a scoket it is just a file without any meaning but then using the command: "bind(sockfd, (struct sockaddr*)&self, sizeof(self));" we bind it means the socket can now listen to connections.
- Now run the server using "./server" and use nc command to communicate with the server.
<img width="214" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/0425c350-c1b3-40c0-8405-19ba7c454d04">
<img width="266" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/674d05e9-ea8a-41cb-a53e-ce0a31015739">

- Expected output:
<img width="361" alt="image" src="https://github.com/shwetasng/DevOps-Bootcamp-Learnings/assets/103261868/c330c09c-62ac-4a19-901c-e6b79655d5c5">





