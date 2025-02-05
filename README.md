# Setting Up SSH for GitHub

This guide will walk you through generating an SSH key and using it to authenticate with GitHub.

## 1. Generate a New SSH Key
If you don't have an existing key, generate a new one:
![Generate Key Pair](<images/Screenshot 2025-02-04 154404 - ssh 1.png>)

```bash
ssh-keygen -t rsa -b 4096 -C "amirbile@hotmail.co.uk"
```

- When prompted, press **Enter** to accept the default file location and enter your key name `amir-gt-key`
- Set a passphrase for added security (optional).

## 3. Add Your SSH Key to the SSH Agent
Ensure the SSH agent is running:

```bash
eval "$(ssh-agent -s)"
```

Then add your key:

```bash
ssh-add ~/.ssh/keyname
```

## 4. Copy Your SSH Key
Copy the public key to your clipboard, pub being your public key:

```bash
cat ~/.ssh/keyname.pub
```

Copy the output and proceed to GitHub.

## 5. Add the SSH Key to GitHub
1. Go to [GitHub SSH Keys](https://github.com/settings/keys).
2. Click **New SSH Key**.
3. Paste your copied key into the **Key** field.
4. Click **Add SSH Key**.

## 6. Test SSH Connection
Verify your connection to GitHub:
![SSH - T confirmation](<images/Screenshot 2025-02-04 154630.png>)

```bash
ssh -T git@github.com
```

If successful, you'll see:
![Successful Authentication]](<images/Screenshot 2025-02-04 154630.png>)
```
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```
## Initialize a New Git Repository

Navigate to your project directory:

```
cd /path/to/your/project
```

Initialize a new Git repository:

```
git init
```

Add your remote repository:

```
git remote add origin git@github.com:Amirdocs/tech-test-ssh-2.git
```

Add files and commit:

```
git add .
git commit -m "Initial commit"
```

Push to GitHub:

```
git push -u origin main
```

If main doesn't exist yet, rename the default branch:

```
git branch -M main
git push -u origin main
```

## 7. Configure Git to Use SSH (Optional)
![Git repo](<images/Screenshot 2025-02-04 155233.png>)

To ensure Git uses SSH instead of HTTPS:

```bash
git config --global user.name "Your Name"
git config --global user.email "your_email@example.com"
git remote set-url origin git@github.com:username/repository.git
```

You're now set up to use SSH with GitHub!
