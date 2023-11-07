# Multiple SSH keys for GitHub and GitLab

## 1. Generate SSH keys

you can use same email address or different emails for keys

```bash
ssh-keygen -t ed25519 -C "test@email.com" -f ~/.ssh/id_rsa_github
ssh-keygen -t ed25519 -C "test2@gmail.com" -f ~/.ssh/id_rsa_gitlab
```

## 2. Copy keys to GitHub and GitLab

```bash
# Copy Public Key to GitHub
cat ~/.ssh/id_rsa_github.pub
copy file content
# Then paste in GitHub panel

# Copy Public Key to GitLab
cat ~/.ssh/id_rsa_gitlab.pub
copy file content
# Then paste in GitLab panel
```

## 3. Starts the SSH-Agent

```
eval `ssh-agent -s`
```

## 4. Add keys to SSH-Agent

```bash
ssh-add ~/.ssh/id_rsa_github
ssh-add ~/.ssh/id_rsa_gitlab
```

## 5. Configuration file

```bash
code ~/.ssh/config
```

**File** `config`

```
# GitHub account
Host github.com
  HostName github.com
  PreferredAuthentications publickey
  IdentityFile ~/.ssh/id_rsa_github

# Testing GitHub connection:
# ssh -T git@github.com
# Hi User! You've successfully authenticated, but GitHub does not
# provide shell access.

# GitLab account
Host gitlab.com
  HostName gitlab.com
  PreferredAuthentications publickey
  IdentityFile ~/.ssh/id_rsa_gitlab

# Testing GitLab connection:
# ssh -T git@gitlab.com
# Welcome to GitLab, @user!
```
