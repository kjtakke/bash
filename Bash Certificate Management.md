# Bash Certificate Management

| Task | Command | Description |
|------|---------|-------------|
| **Generate a Private Key** | `openssl genpkey -algorithm RSA -out private.key -pkeyopt rsa_keygen_bits:2048` | Generates a 2048-bit RSA private key. |
| **Generate a Private Key (ECDSA)** | `openssl ecparam -name prime256v1 -genkey -noout -out private.key` | Generates an ECDSA private key using prime256v1 curve. |
| **Generate a CSR (Certificate Signing Request)** | `openssl req -new -key private.key -out request.csr -subj "/CN=example.com"` | Creates a CSR using an existing private key. |
| **Generate a Self-Signed Certificate** | `openssl req -x509 -new -nodes -key private.key -sha256 -days 365 -out cert.crt` | Generates a self-signed certificate valid for 365 days. |
| **Create a CSR and Key in One Command** | `openssl req -new -newkey rsa:2048 -nodes -keyout private.key -out request.csr` | Generates both a private key and CSR in one step. |
| **View Certificate Details** | `openssl x509 -in cert.crt -text -noout` | Displays details of a certificate. |
| **Verify a Certificate Against a Private Key** | `openssl x509 -noout -modulus -in cert.crt | openssl md5 && openssl rsa -noout -modulus -in private.key | openssl md5` | Ensures the certificate matches the private key. |
| **Verify a CSR** | `openssl req -text -noout -verify -in request.csr` | Checks the details of a CSR. |
| **Verify a Certificate Against a CA** | `openssl verify -CAfile ca.crt cert.crt` | Verifies if a certificate was signed by a specific CA. |
| **Convert DER to PEM** | `openssl x509 -inform der -in cert.der -out cert.pem` | Converts a certificate from DER format to PEM format. |
| **Convert PEM to DER** | `openssl x509 -outform der -in cert.pem -out cert.der` | Converts a certificate from PEM to DER format. |
| **Convert PFX to PEM (With Key)** | `openssl pkcs12 -in cert.pfx -out cert.pem -nodes` | Extracts the certificate and key from a PFX file. |
| **Convert PFX to PEM (Without Key)** | `openssl pkcs12 -in cert.pfx -clcerts -nokeys -out cert.pem` | Extracts only the certificate from a PFX file. |
| **Convert PEM to PFX** | `openssl pkcs12 -export -out cert.pfx -inkey private.key -in cert.crt -certfile ca.crt` | Converts a PEM certificate to a PFX file. |
| **Check Certificate Expiry** | `openssl x509 -enddate -noout -in cert.crt` | Shows the expiry date of a certificate. |
| **List Available CA Certificates** | `openssl x509 -in /etc/ssl/certs/ca-certificates.crt -text -noout` | Lists available CA certificates in the system. |
| **Remove Passphrase from Private Key** | `openssl rsa -in encrypted.key -out decrypted.key` | Removes a passphrase from an encrypted private key. |
| **Create a Certificate Chain File** | `cat cert.crt intermediate.crt rootCA.crt > chain.crt` | Combines multiple certificates into a chain file. |
| **Generate a Diffie-Hellman (DH) Key** | `openssl dhparam -out dhparam.pem 2048` | Generates a 2048-bit DH key for TLS. |
| **Test a TLS Connection** | `openssl s_client -connect example.com:443 -servername example.com` | Tests an SSL/TLS connection to a server. |
| **Extract Public Key from Private Key** | `openssl rsa -in private.key -pubout -out public.key` | Extracts the public key from a private key. |
| **Extract Public Key from Certificate** | `openssl x509 -in cert.crt -pubkey -noout > public.key` | Extracts the public key from a certificate. |