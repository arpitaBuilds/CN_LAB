
#include <stdio.h>

int main() {
    int n, w, lost, i, j;

    printf("Enter no of frames: ");
    scanf("%d", &n);

    printf("Enter window size: ");
    scanf("%d", &w);

    printf("Enter lost frame: ");
    scanf("%d", &lost);

    printf("\n--- Go-Back-N Protocol ---\n");

    for(i = 0; i < n; i += w) {

        printf("\nSending frames: ");

        for(j = i; j < i + w && j < n; j++) {
            printf("%d ", j);
        }

        printf("\n");

        if(lost >= i && lost < i + w && lost < n) {

            printf("Frame %d is lost!\n", lost);

            printf("Retransmitting from frame %d: ", lost);

            for(j = lost; j < i + w && j < n; j++) {
                printf("%d ", j);
            }

            printf("\nAcknowledgment received.\n");
        }
        else {
            printf("All frames acknowledged successfully.\n");
        }
    }

    printf("\nAll frames transmitted.\n");

    return 0;
}
