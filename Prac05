
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <unistd.h>
#include <netinet/in.h>
#include <arpa/inet.h>

#define PORT 10055
#define BUF_SIZE 1024

int main() {
    int sock;
    struct sockaddr_in server;
    char buffer[BUF_SIZE];
    socklen_t len = sizeof(server);

    // Create UDP socket
    sock = socket(AF_INET, SOCK_DGRAM, 0);

    // Prepare server address
    memset(&server, 0, sizeof(server));
    server.sin_family = AF_INET;
    server.sin_port = htons(PORT);
    server.sin_addr.s_addr = inet_addr("127.0.0.1");

    printf("UDP Client started...\n");

    while (1) {
        printf("Enter message: ");
        if (fgets(buffer, BUF_SIZE, stdin) == NULL)
            break;

        // Send message to server
        sendto(sock, buffer, strlen(buffer), 0,
               (struct sockaddr *)&server,
               sizeof(server));

        memset(buffer, 0, BUF_SIZE);

        // Receive echo from server
        int bytes = recvfrom(sock, buffer,
                             BUF_SIZE - 1, 0,
                             (struct sockaddr *)&server,
                             &len);

        if (bytes <= 0)
            break;

        buffer[bytes] = '\0';
        printf("Echo from server: %s", buffer);
    }

    close(sock);
    return 0;
}
