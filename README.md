# My macOS setup

## iTerm setup
---
### Install Homebrew

Install Homebrew using the install command on this page: [Install Homebrew](https://brew.sh/)

---
### Install iTerm2

Install iTerm2 from here: [Download iTerm2](https://iterm2.com/)

---
### Install oh-my-zsh

Install oh-my-zsh by running on the command on this page: [Install oh-my-zsh](https://ohmyz.sh/#install)

---
### Configure iterm2

1. Open iTerm2, go to iTerm2 > Preferences > Profiles > Default > Colors. Select the color preset "Smoooooth".
2. Select the Text tab and increase the font size to 14.

---
### Configure Github and BitBucket

1. Install Git
`brew install git`

2. Set global configuration for Git  
`git config --global user.name "Name"`  
`git config --global user.email "username@emai.com"`  

3. Create SSH Keys for both BitBucket (assuming BitBucket is the primary account) and Github
`ssh-keygen -t rsa -C "bitbucket email"`
Save the key to: `~/.ssh/id_rsa` (default)
Enter the passphrase if necessary

Repeat for Github key
`ssh-keygen -t rsa -C "github email"`
Save the key to: `~/.ssh/id_rsa_gh`
Enter the passphrase if necessary

4. Copy each ssh key to respective repo account
Login to BitBucket, run `pbcopy < ~/.ssh/id_rsa.pub`
Paste the key into the SSH settings of BitBucket.

Login to Github, run `pbcopy < ~/.ssh/id_rsa_gh.pub`
Paste the key into the SSH settings of Github.

5. Create SSH config file
Run `vi ~/.ssh/config`

Create the file with the following information.
Replace <username> with the respective username for the repos.
```
Host *
  UseKeychain yes
  AddKeysToAgent yes

#BitBucket (primary)
  Host bb
  HostName bitbucket.org
  User <username>
  IdentityFile ~/.ssh/id_rsa

#Github (secondary)
  Host gh
  HostName github.com
  User <username>
  IdentityFile ~/.ssh/id_rsa_gh
```

6. Add the keys to SSH
Run:  
`ssh-add ~/.ssh/id_rsa  
 ssh-add ~/.ssh/id_rsa_gh`

7. Create BitBucket and Github directory  
`cd ~/Documents`  
`mkdir bitbucket`  
`mkdir github`  

8. Clone repos to test  
`cd ~/Documents/bitbuckets`  
`git clone <bitbucket_repo_location>`  

`cd ~/Docuemtns/github`  
`git clone <github_repo_location>`  
