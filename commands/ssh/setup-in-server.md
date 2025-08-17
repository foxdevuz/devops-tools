## Here you will learn how to set up public ssh key in your server

>#### Whenever you create a new server you don't have to install ssh manually, it is already installed by default

### 1. Create ID RSA key
```bash
ssh-keygen -t rsa -b 4096 -C "your-email@my-mail.com"
```

### 2. Once you're done in the `~/.ssh` directory you will find two files
- `id_rsa` (private key)
- `id_rsa.pub` (public key)

### 3. Copy the public key to `.ssh/authorized_keys`
```bash
cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
```
### 4. Once you're done you will have the following files in your `~/.ssh` directory
- `id_rsa` (private key)
- `id_rsa.pub` (public key)
- `authorized_keys` (contains the public keys that are allowed to connect to the server)

## After all you can use private key to connect to the server here's how:

### 1. Put the private key in your local machine
```bash
scp user@server_ip:~/.ssh/id_rsa ~/.ssh/
```
> it will ask you for the password of the server
> and if you have already a private key in your local machine you can copy it to another file
> for example:
```bash
scp user@server_ip:~/.ssh/id_rsa ~/.ssh/my_custom_key
```
### 2. Connect to the server using the private key
```bash
ssh -i /path/to/your/ssh/private/key user@server_ip
```