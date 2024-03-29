# Hill Cipher Encryption Project
This is a Python implementation of the Hill Cipher encryption algorithm. The Hill Cipher is a polygraphic substitution cipher that encrypts plaintext by transforming it into a matrix and multiplying it with a key matrix.

## Installation
To use this project, you need to have Python 3 installed on your machine. You can download the latest version of Python from the official website.

Once you have Python 3 installed, you can clone this repository by running the following command in your terminal:
```
git clone https://github.com/your_username/hill-cipher.git
```

## Usage
To use the Hill Cipher encryption algorithm, you need to import the HillCipher function from the hill_cipher.py module.

The HillCipher function takes two arguments:
- message: The plaintext or ciphertext that you want to encrypt or decrypt.
- procedure: The encryption or decryption procedure that you want to use.

There are two procedures that you can use:
- encrypt: Encrypts plaintext using the Hill Cipher algorithm.
- decrypt: Decrypts ciphertext using the Hill Cipher algorithm.

Here's an example of how to use the HillCipher function to encrypt and decrypt a message:
```
from hill_cipher import HillCipher, encrypt, decrypt

message = "linear algebra is easy"

# Encrypt the message
encrypted_message = HillCipher(message.lower(), encrypt)
print(f"After Encryption: {encrypted_message}")

# Decrypt the message
decrypted_message = HillCipher(encrypted_message, decrypt)
print(f"After Decryption: {decrypted_message}")
```
## Algorithm
The Hill Cipher algorithm works by transforming the plaintext into a matrix and multiplying it with a key matrix to produce ciphertext. To decrypt the ciphertext, the inverse of the key matrix is used to multiply it with the ciphertext matrix.

The key matrix and its inverse are generated by the user and are stored in the keyMatrix and DecryptMatrix variables, respectively. The alphaDict variable is a dictionary that maps each character to a number and vice versa.

The encrypt function takes a message vector, the length of the message, and an empty cipher matrix as input. It multiplies the key matrix with the message vector to produce the cipher matrix, which is then returned.

The decrypt function takes a message vector, the length of the message, and an empty cipher matrix as input. It first calculates the inverse of the key matrix using the moduloDecrypt function. It then multiplies the inverse key matrix with the message vector to produce the cipher matrix, which is then returned.

The HillCipher function takes a message and a procedure as input. It first transforms the message into a message vector using the alphaDict dictionary. It then calls the specified procedure on the message vector to produce the ciphertext or plaintext, which is then transformed back into a message using the alphaDict dictionary.
