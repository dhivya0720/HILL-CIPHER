# HILL CIPHER
HILL CIPHER
EX. NO: 3 AIM:
 

IMPLEMENTATION OF HILL CIPHER
 
## To write a C program to implement the hill cipher substitution techniques.

## DESCRIPTION:

Each letter is represented by a number modulo 26. Often the simple scheme A = 0, B
= 1... Z = 25, is used, but this is not an essential feature of the cipher. To encrypt a message, each block of n letters is  multiplied by an invertible n × n matrix, against modulus 26. To
decrypt the message, each block is multiplied by the inverse of the m trix used for
 
encryption. The matrix used
 
for encryption is the cipher key, and it sho
 
ld be chosen
 
randomly from the set of invertible n × n matrices (modulo 26).


## ALGORITHM:

STEP-1: Read the plain text and key from the user. STEP-2: Split the plain text into groups of length three. STEP-3: Arrange the keyword in a 3*3 matrix.
STEP-4: Multiply the two matrices to obtain the cipher text of length three.
STEP-5: Combine all these groups to get the complete cipher text.

## PROGRAM 
```
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int key[3][3] = {
    {6, 24, 1},
    {13, 16, 10},
    {20, 17, 15}
};

int invkey[3][3] = {
    {8, 5, 10},
    {21, 8, 21},
    {21, 12, 8}
};

void hill(char text[], int matrix[3][3], char result[]) {
    int i, j, k, sum, n = strlen(text);

    for (i = 0; i < n; i += 3) {
        for (j = 0; j < 3; j++) {
            sum = 0;
            for (k = 0; k < 3; k++)
                sum += (text[i + k] - 'A') * matrix[k][j];

            result[i + j] = 'A' + ((sum % 26 + 26) % 26);
        }
    }
    result[n] = '\0';
}

int main() {
    char msg[1000], enc[1000], dec[1000];
    int i, len;

    printf("Enter plaintext: ");
    fgets(msg, sizeof(msg), stdin);
    msg[strcspn(msg, "\n")] = '\0';

    len = 0;
    for (i = 0; msg[i]; i++) {
        if (isalpha((unsigned char)msg[i]))
            msg[len++] = toupper((unsigned char)msg[i]);
    }
    msg[len] = '\0';

    while (len % 3 != 0)
        msg[len++] = 'X';
    msg[len] = '\0';

    hill(msg, key, enc);
    hill(enc, invkey, dec);

    printf("Padded plaintext: %s\n", msg);
    printf("Encrypted text: %s\n", enc);
    printf("Decrypted text: %s\n", dec);

    return 0;
}
```

## OUTPUT
<img width="532" height="292" alt="image" src="https://github.com/user-attachments/assets/ba206bb8-813f-4a65-a828-73bb94da825f" />



## RESULT
