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
  ````

- Verify the signature matches the file (try to rerun after changing the text)

  ```sh
  openssl dgst -sha256 -verify public.pem -signature signature.bin message.txt
  ```

- Write the signature as Base64 encoded

  ```sh
  base64 signature.bin > signature.b64
  ```

## References

- [JWT Builder](http://jwtbuilder.jamiekurtz.com/): Simple site for exploring how JWTs are constructed. Mind these are not signed by any authority, and hence rather useless.

- [OpenSSL](https://openssl-library.org/): Standard cryptographic tooling
