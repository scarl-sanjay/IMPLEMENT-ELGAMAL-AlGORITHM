# EXP-12-IMPLEMENT-ELGAMAL-AlGORITHM

## AIM:
To write a program to implement Elgamal Algorithm.

## ALGORITHM:

### STEP-1: 
Input large prime number, base, and private key
### STEP-2:
Calculate the public key
### STEP-3: 
Input message to encrypt
### STEP-4: 
Input random ephemeral key
### STEP-5: 
ElGamal Encryption and ElGamal Decryption is done.

## PROGRAM:
```c
#include <stdio.h>
#include <math.h>
#include <stdlib.h>
int mod_exp(int base, int exp, int mod) {
int result = 1;
base = base % mod;
while (exp > 0) {
if (exp % 2 == 1) {
result = (result * base) % mod;
}
exp = exp >> 1; 
base = (base * base) % mod;
}
return result;
}
int gcd(int a, int b) {
if (b == 0)
return a;
else
return gcd(b, a % b);

}
int main() {
int p, g, x; 
int h, y;
int message, k; 
int c1, c2, decrypted_message; 
printf("\n\n *******Elgamal encryption and decryption*******\n\n SANJAY S 212223040184\n\n");
printf("Enter a large prime number (p): ");
scanf("%d", &p);
printf("Enter a primiƟve root of p (g): ");
scanf("%d", &g);
printf("Enter the private key (x): ");
scanf("%d", &x);
h = mod_exp(g, x, p);
printf("Public key (h) = %d\n", h);

printf("Enter the message to encrypt (as an integer less than p): ");
scanf("%d", &message);
do {
printf("Enter the ephemeral key (k) such that gcd(k, p-1) = 1: ");
scanf("%d", &k);


} while (gcd(k, p - 1) != 1);
c1 = mod_exp(g, k, p); 
c2 = (message * mod_exp(h, k, p)) % p; 
printf("Ciphertext (c1, c2) = (%d, %d)\n", c1, c2);

int inverse = mod_exp(c1, p - 1 - x, p); 
decrypted_message = (c2 * inverse) % p; 

printf("Decrypted message = %d\n", decrypted_message);
return 0;
}
```
## Output:

![image](https://github.com/user-attachments/assets/cf21eabe-896b-496e-9dae-6baa5b1d5938)

## Result:
Thus the Elgamal algorithm had been implemented successfully.
