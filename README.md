# EX-NO-13-MESSAGE-AUTHENTICATION-CODE-MAC

## AIM:
To implement MESSAGE AUTHENTICATION CODE(MAC)

## ALGORITHM:

1. Message Authentication Code (MAC) is a cryptographic technique used to verify the integrity and authenticity of a message by using a secret key.

2. Initialization:
   - Choose a cryptographic hash function \( H \) (e.g., SHA-256) and a secret key \( K \).
   - The message \( M \) to be authenticated is input along with the secret key \( K \).

3. MAC Generation:
   - Compute the MAC by applying the hash function to the combination of the message \( M \) and the secret key \( K \): 
     \[
     \text{MAC}(M, K) = H(K || M)
     \]
     where \( || \) denotes concatenation of \( K \) and \( M \).

4. Verification:
   - The recipient, who knows the secret key \( K \), computes the MAC using the received message \( M \) and the same hash function.
   - The recipient compares the computed MAC with the received MAC. If they match, the message is authentic and unchanged.

5. Security: The security of the MAC relies on the secret key \( K \) and the strength of the hash function \( H \), ensuring that an attacker cannot forge a valid MAC without knowledge of the key.

## Program:

```
#include <stdio.h>
#include <string.h>
#include <ctype.h>
void encrypt(char message[], int shift);
void decrypt(char message[], int shift);
int main() {
 char message[100];
 int shift;
 printf("********** MAC [ Message Authentication Code ] **********\n\n");
 printf("Enter a message to encrypt: ");
 fgets(message, sizeof(message), stdin);
 printf("Enter the shift value: ");
 scanf("%d", &shift);
 encrypt(message, shift);
 printf("\nEncrypted message: %s\n", message);
 decrypt(message, shift);
 printf("Decrypted message: %s\n", message);
 return 0;
}
void encrypt(char message[], int shift) {
 for (int i = 0; message[i] != '\0'; ++i) {
 char ch = message[i];
 if (islower(ch)) {
 message[i] = ((ch - 'a' + shift) % 26) + 'a';
 }
 else if (isupper(ch)) {
 message[i] = ((ch - 'A' + shift) % 26) + 'A';
 }
 }
}
void decrypt(char message[], int shift) {
 for (int i = 0; message[i] != '\0'; ++i) {
 char ch = message[i];
 if (islower(ch)) {
 message[i] = ((ch - 'a' - shift + 26) % 26) + 'a';
 }
 else if (isupper(ch)) {
 message[i] = ((ch - 'A' - shift + 26) % 26) + 'A';
 }
 }
}
```


## Output:
![Screenshot 2024-11-11 181810](https://github.com/user-attachments/assets/32399712-57a8-4c90-906c-f3db01aec84d)


## Result:
The program is executed successfully.
