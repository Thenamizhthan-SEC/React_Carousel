# Ex05 Image Carousel
## Date: 08/06/2026

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM
~~~
#include <stdio.h>
#include <string.h>

#define MAC_SIZE 32 // Define MAC size in bytes

// Function to compute a simple MAC using XOR
void computeMAC(const char *key, const char *message, char *mac) {
    int key_len = strlen(key);
    int msg_len = strlen(message);
    
    // XOR the key and message, repeating if necessary
    for (int i = 0; i < MAC_SIZE; i++) {
        mac[i] = key[i % key_len] ^ message[i % msg_len]; // Simple XOR operation
    }
    mac[MAC_SIZE] = '\0'; // Null-terminate the MAC string
}

int main() {
    char key[100], message[100];
    char mac[MAC_SIZE + 1]; // Buffer for MAC (+1 for null terminator)
    char receivedMAC[MAC_SIZE + 1]; // Buffer for input of received MAC

    // Step 1: Input secret key
    printf("Enter the secret key: ");
    scanf("%s", key);

    // Step 2: Input the message
    printf("Enter the message: ");
    scanf("%s", message);

    // Step 3: Compute the MAC
    computeMAC(key, message, mac);

    // Step 4: Display the computed MAC in hexadecimal
    printf("Computed MAC (in hex): ");
    for (int i = 0; i < MAC_SIZE; i++) {
        printf("%02x", (unsigned char)mac[i]); // Print each byte as hex
    }
    printf("\n");

    // Step 5: Input the received MAC (for verification)
    printf("Enter the received MAC (as hex): ");
    for (int i = 0; i < MAC_SIZE; i++) {
        scanf("%02hhx", &receivedMAC[i]);
    }

    // Compare the computed MAC with the received MAC
    if (memcmp(mac, receivedMAC, MAC_SIZE) == 0) {
        printf("MAC verification successful. Message is authentic.\n");
    } else {
        printf("MAC verification failed. Message is not authentic.\n");
    }

    return 0;
}
~~~
## OUTPUT
<img width="797" height="377" alt="image" src="https://github.com/user-attachments/assets/501d932e-de3c-4296-a44c-099a53b512df" />


## RESULT
The program for creating Image Carousel using React is executed successfully.
