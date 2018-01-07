# Encode / Decode files using OpenSSL

## Encoding

    openssl enc -e -a -aes-256-cbc  -in C:/file.zip -out C:/file.txt

    
## Decoding

    openssl enc -d -a -aes-256-cbc  -in C:/file.txt -out C:/file.zip
