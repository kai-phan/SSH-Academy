# SSH-Academy
Learn SSH

## Client/Server communication
- SSH is the client
- SSHD is server
- The server must have SSHD installed and running or you will not be able to connect using SSH

## Authentication method
- Password
    ```bash
      ssh {user}@{host}
    ```
- Key pair (recommended)
- Host based

## Simple way to create SSH key pair

```bash
  ssh-keygen
```
- ~/.ssh/id_rsa (private key)
- ~/.ssh/id_rsa.pub (public key)
- Public key goes into server "authorized_keys" file

## With argument algorithm and key size 

```bash
  ssh-keygen -t rsa -b 4096
  ssh-keygen -t dsa 
  ssh-keygen -t ecdsa -b 521
  ssh-keygen -t ed25519
```

## AWS EC2 example
1. Launch EC2 instance
2. Create key pairs, and download the .pem file
3. Edit public viewable .pem file
  ```bash
    chmod 400 "abc.pem"
  ```
4. Connect to EC2 instance through SSH command
  ```bash
    ssh -i "abc.pem" {user}@{host}
  ```
  Host can be IP address or public DNS
5. Check public key in remote server
  ```bash
    cat ~/.ssh/authorized_keys
  ```
