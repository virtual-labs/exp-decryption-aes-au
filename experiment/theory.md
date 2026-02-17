# Experiment 6: AES Ciphertext Decryption

## AES Decryption Process

The AES is a symmetric block cipher that transforms data securely through a series of mathematical operations performed on 128-bit blocks. Since AES is symmetric, the same secret key is used for both encryption and decryption. While the encryption process applies a set of forward transformations, decryption uses the corresponding inverse operations to reconstruct the original plaintext from the ciphertext.

AES supports three key sizes—128, 192, and 256 bits—which correspond to 10, 12, and 14 decryption rounds, respectively. Regardless of the key size, AES decryption proceeds by reversing the steps of encryption in the exact opposite order and applying the round keys in reverse sequence. These round keys are generated through the AES key expansion process and are essential for both directions of operation.

## AES Decryption Transformations

AES decryption applies the following inverse transformations:

### Step 1: Inverse ShiftRows

This step cyclically shifts the rows of the state matrix in the opposite direction compared to encryption. It restores the original row-byte arrangement and is essential for reversing diffusion introduced during encryption.

### Step 2: Inverse SubBytes

Each byte is substituted using the inverse S-box, which is mathematically derived to reverse the nonlinear substitution applied during SubBytes in encryption. This ensures the restoration of the correct byte values before further transformations.

### Step 3: Inverse MixColumns  
*(applied in all rounds except the final round)*

Each column undergoes a matrix multiplication with an inverse transformation matrix in the finite field GF(2⁸). This reverses the mixing of bytes performed during the MixColumns step in encryption, thus undoing intra-column diffusion.

### Step 4: AddRoundKey

In this step, the round key corresponding to the current round (applied in reverse order) is XORed with the state. Since XOR is self-inverse, this operation perfectly undoes the addition of the round key applied during the encryption round.

The decryption process begins with AddRoundKey using the last round key, followed by the inverse operations round-by-round. The final decryption step excludes the Inverse MixColumns transformation to maintain structural symmetry with the encryption process.