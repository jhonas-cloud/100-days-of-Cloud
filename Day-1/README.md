# 100 Days of Cloud - Day 1

## Creating a Key Pair in EC2 Instance

### Overview
A key pair is a set of security credentials consisting of a public key and a private key. AWS uses key pairs to encrypt and decrypt login information for EC2 instances. This is an essential first step before launching any EC2 instances.

### What is a Key Pair?
- **Public Key**: Stored on the EC2 instance and used to encrypt data
- **Private Key**: Downloaded and stored locally; used to decrypt data and connect to instances
- **Purpose**: Provides secure SSH access to EC2 instances

### Why Key Pairs are Important
1. **Security**: Replaces traditional username/password authentication with cryptographic keys
2. **Automation**: Enables automated deployments and scripts
3. **Access Control**: Only those with the private key can access the instance
4. **Non-repudiation**: Proves your identity when accessing instances

---

## Steps to Create a Key Pair in AWS Console

### Method 1: Using AWS Management Console

1. **Navigate to EC2 Dashboard**
   - Go to [AWS Console](https://console.aws.amazon.com/)
   - Select the desired region (top-right corner)
   - Click on "EC2" under Compute services

2. **Access Key Pairs Section**
   - In the left sidebar, under "Network & Security"
   - Click on "Key Pairs"

3. **Create a New Key Pair**
   - Click the "Create key pair" button
   - Enter a descriptive name (e.g., `my-ec2-key`, `day1-keypair`)
   - Select key pair type:
     - **RSA** (recommended for most use cases)
     - **ED25519** (more modern, smaller key size)
   - Select private key file format:
     - **.pem** (for Linux/Mac SSH clients)
     - **.ppk** (for PuTTY on Windows)
   - Click "Create key pair"

4. **Download and Secure**
   - The private key file will automatically download
   - Store it in a secure location
   - Set proper permissions (Linux/Mac): `chmod 400 my-ec2-key.pem`
   - **Never** share your private key

### Method 2: Using AWS CLI

```bash
aws ec2 create-key-pair --key-name my-ec2-key --query 'KeyMaterial' --output text > my-ec2-key.pem

# Set correct permissions
chmod 400 my-ec2-key.pem
```

---

## Using Your Key Pair to Connect to an Instance

### SSH Connection (Linux/Mac)
```bash
ssh -i /path/to/my-ec2-key.pem ec2-user@<instance-public-ip>
```

### SSH Connection (Windows - using PuTTY)
1. Convert `.pem` file to `.ppk` using PuTTYgen
2. Open PuTTY and load the `.ppk` file
3. Connect to the instance IP address

### SSH Connection (Windows - using WSL/Git Bash)
```bash
ssh -i ~/Documents/my-ec2-key.pem ec2-user@<instance-public-ip>
```

---

## Best Practices

✅ **DO:**
- Store private keys in a secure location (e.g., `~/.ssh/`)
- Set restrictive permissions: `chmod 400 key.pem`
- Use descriptive key pair names
- Create separate key pairs for different environments (dev, staging, prod)
- Backup your private key securely
- Rotate key pairs periodically

❌ **DON'T:**
- Share your private key with anyone
- Commit private keys to version control
- Store private keys in unsecured cloud storage
- Use the same key pair across multiple AWS accounts
- Keep default permissions on key files

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| "Permissions are too open" error | Run `chmod 400 key.pem` |
| "Connection refused" | Check security group rules allow SSH (port 22) |
| "Host key verification failed" | Add `-o StrictHostKeyChecking=no` to SSH command |
| Lost private key | Generate a new key pair and relaunch instance |

---

## Summary
Creating a key pair is the foundation of secure EC2 access. Always remember to:
1. Store your private key securely
2. Never share it
3. Use appropriate file permissions
4. Keep backups in a safe location

**Day 1 Complete!** ✓
