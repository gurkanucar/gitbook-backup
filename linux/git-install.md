# Git Install

run scripts below to install git and configure ssh

```bash
sudo apt install git -y
git --version
git config --global user.name "yourname"
git config --global user.email "yourmail"
git config --list

#create ssh keygen
ssh-keygen -t rsa -b 4096 -C "yourmail"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
cat ~/.ssh/id_rsa.pub

# Generate SSH key (Ed25519 - Preferred)
ssh-keygen -t ed25519 -C "your-email@example.com"
ssh-add ~/.ssh/id_ed25519
cat ~/.ssh/id_ed25519.pub
ssh-add -l

# Configure Git to store credentials permanently (use with caution)
git config --global credential.helper store






```
