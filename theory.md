# AES Decryption Process
Decryption in AES involves reversing the encryption process, transforming ciphertext back into its original plaintext using the same key that was used for encryption. The decryption process consists of several steps:

## Key Expansion
Before decryption, the original encryption key undergoes a key expansion process. This process generates a set of round keys that are used in the subsequent decryption rounds. The number of rounds depends on the key size: 10 rounds for 128-bit keys, 12 rounds for 192-bit keys, and 14 rounds for 256-bit keys.

## Initial Round Key Addition
In the first step of decryption, the last round key is added to the ciphertext. This step is essentially the reverse of the initial round key addition in encryption.

## Inverse Round Transformation
The inverse round transformation is a key step in decryption. It consists of four operations performed in reverse order compared to encryption:

- **Inverse SubBytes:** Each byte of the state is replaced with its inverse in the AES S-box.
- **Inverse ShiftRows:** Bytes in the rows are shifted to the right, with the shift distance increasing for each subsequent row.
- **Inverse MixColumns:** The columns of the state are mixed using a fixed matrix that has an inverse.
- **AddRoundKey:** The round key is XORed with the state.

## Repeat Inverse Round Transformation
The inverse round transformation is repeated for the specified number of rounds (10, 12, or 14), depending on the key size.

## Final Round
In the final round, the decryption process involves the following steps in sequence: performing Inverse SubBytes, applying Inverse ShiftRows, and then adding the round key through the AddRoundKey operation.
