> [!CAUTION]
>**Roots of Trust**
>
> Cryptographic identities are not to be taken lightly. Possession of a private key means **you can act fully in the identity’s stead**. Whether that’s your personal identity or one delegated to you on behalf of others.
>
> Unlike physical documents (e.g., passports or vehicle registrations), **roots of trust are even harder to exchange or revoke**. Once compromised, they often require replacing entire chains of trust, not just reissuing a card or certificate. Treat them with extreme care.

## Connection

- **Identity Proofing** → *Birth Certificate*  
  Establishes that you exist; initial root of trust.

- **Ownership Verification** → *Vehicle Identity*  
  Confirms this specific "thing" is yours.

- **Enforcement / Control** → *Roadside Vehicle Check*  
  Authorities validate documents and ensure compliance.

- **Decision Authority** → *Who decides?*  
  Defines who grants or denies access.

- **Execution / Enforcement** → *Who enforces?*  
  The party applying the decision in practice.

- **Verification Mechanism** → *How is it verified?*  
  The method of checking (documents, signatures, cryptography).

## Command Reference

- Generate a private key (identity)

  ```sh
  openssl genpkey -algorithm RSA -out private.pem -pkeyopt rsa_keygen_bits:2048
  ```

- Create a public key from the private key

  ```sh
  openssl rsa -pubout -in private.pem -out public.pem
  ```

- Create a simple text file

  ```sh
  echo "I am a backend developer!" > message.txt
  ```

- Create a signature for that file

  ```sh
  openssl dgst -sha256 -sign private.pem -out signature.bin message.txt
  ```

- Verify the signature matches the file (try to rerun after changing the text)

  ```sh
  openssl dgst -sha256 -verify public.pem -signature signature.bin message.txt
  ```

- Write the signature as Base64 encoded

  ```sh
  base64 signature.bin > signature.b64
  ```

## Sketches

- ![Sketches](/docs/iam-introduction.png)

## References

- [JWT Builder](http://jwtbuilder.jamiekurtz.com/): Simple site for exploring how JWTs are constructed. Mind these are not signed by any authority, and hence rather useless.

- [OpenSSL](https://openssl-library.org/): Standard cryptographic tooling
