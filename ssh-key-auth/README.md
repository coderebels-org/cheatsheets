# ssh with key/certificate (without password)

Precondition: openssh is installed on client and server.

## Step 1: generate key pair (if not already existing):

```
ssh-keygen -t rsa
```

## Step 2: Copy public key (id_rsa.pub) to server:

```
ssh-copy-id -i ~/.ssh/id_rsa.pub user@remote-system
```
