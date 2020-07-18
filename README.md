# AES_256-Python
A file encryption tool written with Python 3 using AES-256 bits, scrypt and SHA3-512 algorithms.

AES-Python encrypts|decrypts a file or all files in a folder (even files in subfolders).

# Requirements
- [Pycryptodome](https://pycryptodome.readthedocs.io/en/latest/)

Run `pip3 install -r requirements.txt`

# Usage
Run `python3 AES.py -f [path of the file or folder] -e|d [e for encrypt | d for decrypt]`

and follow instructions on the terminal.

# Explanation
- The AES key is generated by the scrypt key derivation algorithm using the password and a random 32 bytes salt.
- The password is hashed with SHA3-512 with the same salt than the AES-256 key
- Salt, hashed password and the initialisation vector are stored at the beginning of the new encrypted file
- Data of the plain file is encrypted through a 65kb buffer and stored into the new encrypted file
- The plain file is removed

# Example
> **Plain text:** 
Hello, I'm a test for Gaëtan Serré's Python-AES repository.

> **Encrypted text with the password azerty:** 
ïÅñœËÂv—9π™XÏ~,Ï'”Ü^k#35=˛öUóßÚ˛72;∆ı
µ» ŒôP†Rı0O(4Ühj}—4Òw›D=ûby∫⁄;ï9Rs˝mRßˇ˘Ÿ÷—¥≠AıJVmÅ0ÅèÁxë⁄ ÂézµíØÆW+Ò%€8≠ï:‰–füïlH¥5≠I12˚Q≈≥ZhU≥BÕüN√÷êTKÆ∞ÖwâË#`~

- The 32 first bytes are the salt used in the SHA3-512 hashing and in the scrypt's derivation key
- The next 16 bytes are the initialization vector for AES-256
- The next 64 bytes are the hashed password
- The next bytes are of the encrypted data



# Warning
Please save your password carefully. You will not be able to retrieve your data otherwise.
