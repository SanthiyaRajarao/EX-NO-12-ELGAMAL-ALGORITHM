# EX-NO-12-ELGAMAL-ALGORITHM

## AIM:
To Implement ELGAMAL ALGORITHM

<BR>
NAME:SANTHIYA R

REG NO: 212223230192


## ALGORITHM:

1. ElGamal Algorithm is a public-key cryptosystem based on the Diffie-Hellman key exchange and relies on the difficulty of solving the discrete logarithm problem.

2. Initialization:
   - Select a large prime \( p \) and a primitive root \( g \) modulo \( p \) (these are public values).
   - The receiver chooses a private key \( x \) (a random integer), and computes the corresponding public key \( y = g^x \mod p \).

3. Key Generation:
   - The public key is \( (p, g, y) \), and the private key is \( x \).

4. Encryption:
   - The sender picks a random integer \( k \), computes \( c_1 = g^k \mod p \), and \( c_2 = m \times y^k \mod p \), where \( m \) is the message.
   - The ciphertext is the pair \( (c_1, c_2) \).

5. Decryption:
   - The receiver computes \( s = c_1^x \mod p \), and then calculates the plaintext message \( m = c_2 \times s^{-1} \mod p \), where \( s^{-1} \) is the modular inverse of \( s \).

6. Security: The security of the ElGamal algorithm relies on the difficulty of solving the discrete logarithm problem in a large prime field, making it secure for encryption.

## Program:
```
def modExp(base, exp, mod):
    result = 1

    while exp > 0:
        if exp % 2 == 1:
            result = (result * base) % mod

        base = (base * base) % mod
        exp = exp // 2

    return result

p = int(input("Enter prime number: "))
g = int(input("Enter generator value: "))

privateKey = int(input("Enter private key: "))

publicKey = modExp(g, privateKey, p)

print("Public Key:", publicKey)

message = int(input("Enter message: "))
k = int(input("Enter random k value: "))

c1 = modExp(g, k, p)
c2 = (message * modExp(publicKey, k, p)) % p

print("Encrypted Message:", c1, c2)

decrypted = (c2 * modExp(c1, p - 1 - privateKey, p)) % p

print("Decrypted Message:", decrypted)
```


## Output:



<img width="1168" height="847" alt="Screenshot 2026-05-23 215754" src="https://github.com/user-attachments/assets/6bbdc7ce-f74a-478d-808b-1e8b8b0f5a17" />



## Result:
The program is executed successfully.






