##Learn From Ananth:   base64 -d <file-name>

#1. Encryption  (When we create Customer managed keys: In Alias I typed tutorial)
aws kms encrypt --key-id alias/tutorial --plaintext fileb://ExampleSecretFile.txt --output text --query CiphertextBlob --region <kms-region, eg us-east-1> > ExampleSecretFileEncrypted.base64

#2. base64 decode for Linux or Mac OS
cat ExampleSecretFileEncrypted.base64 | base64 --decode > ExampleSecretFileEncrypted

#3. decryption
aws kms decrypt --ciphertext-blob fileb://ExampleSecretFileEncrypted --output text --query Plaintext > ExampleFileDecrypted.base64 --region us-east-1

#4. base64 decode for Linux or Mac OS
cat ExampleFileDecrypted.base64 | base64 --decode > ExampleFileDecrypted.txt
