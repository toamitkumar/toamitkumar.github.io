---
showonlyimage: true
title:      "Managing multiple SSH Keys with Github & Gitlab"
subtitle:   "SSH Keys - multiple GitHub account, Gitlab accounts"
excerpt: "SSH Keys - multiple GitHub account, Gitlab accounts"
description: ""
date:       2012-08-05
author:    Amit Kumar
image: "img/home-bg.jpg"
draft: false

tags:
    - multiple SSH keys
    - github
    - gitlab
    - SSH
    - SSH Config

categories: [ Tech ]
URL: "/2012/08/05/manage-multiple-ssh-github-gitlab/"
---

I have always stumbled on this problem of managing SSH keys for multiple Git based SCM (Gitlab, GitHub) including multiple GitHub accounts.

If you've single account - adding the [SSH keys](https://help.github.com/articles/generating-ssh-keys) on your github or gitlab is simple. 

I currently have the following accounts:

###### Github
> - 1 personal account
> - 2 behind the firewall (corporate accounts)

###### Gitlab
> - 1 personal account
> - 1 corporate account

If ever face a problem like this, it is best to create a `ssh-config` file which aggregates all your SSH keys. You must follow the steps below:

##### 1. Generate SSH keys for each account and give a name accordingly

Follow the command below to generate SSH keys for each account on GitHub or Gitlab

```
cd ~/.ssh
ssh-keygen -t rsa -C "your-email@abc.com" -f ~/.ssh/id_rsa_account-1-github
ssh-keygen -t rsa -C "your-email@abc.com" -f ~/.ssh/id_rsa_account-2-github

ssh-keygen -t rsa -C "your-email@abc.com" -f ~/.ssh/id_rsa_account-1-gitlab
ssh-keygen -t rsa -C "your-email@abc.com" -f ~/.ssh/id_rsa_account-2-gitlab
```

This should produce multiple pairs of private and public keys:

```
- id_rsa_account-1-github
- id_rsa_account-1-github.pub

- id_rsa_account-2-github
- id_rsa_account-2-github.pub
.....
```

##### 2. Add the public key to the respective account on GitHub or Gitlab

Copy the text under each public key and paste them content for each account on GitHub & Gitlab (this should be easy)

##### 3. Create and map the keys in a Config file

Next create a `config` file under `~/.ssh` directory with the following content:

```
Host github.com
  User git
  Port 22
  Hostname github.com
  IdentityFile ~/.ssh/id_rsa_account-1-github
  TCPKeepAlive yes
  IdentitiesOnly yes
  Hostname github.com
  IdentityFile ~/.ssh/id_rsa_account-2-github

Host gitlab.com
  User git
  Port 22
  Hostname gitlab.com
  IdentityFile ~/.ssh/id_rsa_account-1-gitlab
  TCPKeepAlive yes
  IdentitiesOnly yes
  Hostname gitlab.com
  IdentityFile ~/.ssh/id_rsa_account-2-gitlab
```

Let's validate the settings through a quick CLI:

```
ssh -vT git@github.com
```

You should get a verbose output with successful autheticated message:

```
Hi <user account>! You've successfully authenticated, but GitHub does not provide shell access.
```

Hope it helps!
