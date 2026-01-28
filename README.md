# VIGENERE-CIPHER
## EX. NO: 4
 

## IMPLEMETATION OF VIGENERE CIPHER
 

## AIM:

To implement the Vigenere Cipher substitution technique using C program.

## DESCRIPTION:

To encrypt, a table of alphabets can be used, termed a tabula recta, Vigenère square,or Vigenère table. It consists of the alphabet written out 26 times in differnt rows, each
 
alphabet shifted cyclically to the left compared to the previous alphabet, corresponding to the 26 possible Caesar ciphers. At different points in the encryption process, the cipher uses adifferent alphabet from one of the rows. The alphabet used at each point repeating keyword.depends on a Each row starts with a key letter. The remainder of the row holds the letters A to Z. Although there are 26 key rows shown, you will only use as many keys as there are unique letters in the key string, here just 5 keys, {L, E, M, O, N}. For successive letters of the message, we are going to take successive letters of the key string, and encipher each message letter using its corresponding key row. Choose the next letter of the key, go along that row to find the column heading that	atches the message character; the letter at the intersection of
[key-row, msg-col] is the enciphered letter.


## ALGORITHM:

STEP-1: Arrange the alphabets in row and column of a 26*26 matrix.
STEP-2: Circulate the alphabets in each row to position left such that the first letter is attached to last.
STEP-3: Repeat this process for all 26 rows and construct the final key matrix.
STEP-4: The keyword and the plain text is read from the user.
STEP-5: The characters in the keyword are repeated sequentially so as to match with that of the plain text.
STEP-6: Pick the first letter of the plain text and that of the keyword as the row indices and column indices respectively.
STEP-7: The junction character where these two meet forms the cipher character.
STEP-8: Repeat the above steps to generate the entire cipher text.


## PROGRAM

```
#include <stdio.h>
#include <string.h>
#include <ctype.h>

#define MAX 200

/* Function to generate repeating key */
void generateKey(char str[], char key[], char newKey[])
{
    int i, j = 0;
    int len = strlen(str);
    int keyLen = strlen(key);

    for (i = 0; i < len; i++)
    {
        newKey[i] = key[j];
        j = (j + 1) % keyLen;
    }
    newKey[len] = '\0';
}

/* Function to encrypt plaintext */
void cipherText(char str[], char key[], char cipher[])
{
    int i;
    for (i = 0; str[i] != '\0'; i++)
        cipher[i] = ((str[i] - 'A') + (key[i] - 'A')) % 26 + 'A';

    cipher[i] = '\0';
}

/* Function to decrypt ciphertext */
void originalText(char cipher[], char key[], char original[])
{
    int i;
    for (i = 0; cipher[i] != '\0'; i++)
        original[i] = ((cipher[i] - key[i] + 26) % 26) + 'A';

    original[i] = '\0';
}

int main()
{
    char str[MAX] = "GEEKSFORGEEKS";
    char keyword[MAX] = "AYUSH";
    char key[MAX], cipher[MAX], original[MAX];

    /* Convert plaintext to uppercase */
    for (int i = 0; str[i]; i++)
        str[i] = toupper(str[i]);

    /* Convert keyword to uppercase */
    for (int i = 0; keyword[i]; i++)
        keyword[i] = toupper(keyword[i]);

    generateKey(str, keyword, key);

    cipherText(str, key, cipher);
    printf("Ciphertext : %s\n", cipher);

    originalText(cipher, key, original);
    printf("Original/Decrypted Text : %s\n", original);

    return 0;
}

```

## OUTPUT
<img width="892" height="535" alt="image" src="https://github.com/user-attachments/assets/d4223492-92f1-4b8e-a5a7-4d11f431d5de" />


## RESULT

Thus the program to implement the Vigenere Cipher substitution technique using C program is done successfully.
