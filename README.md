The Odin Project

Started: Tue Jan 10, 2023

Updated: Sat Aug 12, 2023

# Setting up Git

## Step 1: Install Git on MacOS

### Step 1.0: Install Homebrew

After meeting the [requirements](https://docs.brew.sh/Installation#macos-requirements)

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### Step 1.1: Update Git to latest version

```
brew install git
```

### Step 1.2: Verify version

```
git --version
```

## Step 2: Configure Git and Github

### Step 2.1: Create a [Github](https://github.com/) account

### Step 2.2: Setup Git

To enable Git to associate your local work with your GitHub account and show who contributed, use the commands below by replacing the quotes with your own information.

```
git config --global user.name <yourusername>
git config --global user.email <youremail>
```

OR use the private Github email add

```
git config --global user.email "123456789+odin@users.noreply.github.com" # Remember to use your own private GitHub email here.
```

GitHub has updated the default branch for new repositories to 'main' from 'master'. You can adjust your Git settings with the following command to reflect this change:

```
git config --global init.defaultBranch main
```

During The Odin Project, it's recommended to set your default branch reconciliation behavior to merging. You can achieve this by using the following command as part of the Git setup.

```
git config --global pull.rebase false
```

To confirm everything is working correctly, run these commands and check if the output matches your name and email.

```
git config --get user.name
git config --get user.email
```

**for MacOS:** Execute these commands to instruct Git to ignore .DS_Store files, which Finder generates when viewing folders. These files store metadata like thumbnails and, unless ignored, can clutter your commits.

```
echo .DS_Store >> ~/.gitignore_global
git config --global core.excludesfile ~/.gitignore_global
```

### Step 2.3: Create an SSH Key

An SSH key functions as a highly secure identifier, similar to a lengthy password, for your machine. GitHub employs SSH keys to enable seamless repository uploads without requiring repeated username and password input.

To check for an existing Ed25519 algorithm SSH key, enter the command in the terminal and match the output with the provided information.

```
ls ~/.ssh/id_ed25519.pub
```

To create a new SSH key:

```
ssh-keygen -t ed25519 -C <youremail>
```

If prompted for a save location, just press enter
Enter password if desired

### Step 2.4: Link SSH key with Github

Inform GitHub about your SSH key to enable password-free code pushes.
Follow these steps:

**Navigate to SSH Key Setup:**
Log in to GitHub and click your profile picture in the upper-right corner. Choose 'Settings' from the drop-down menu.

**Add Your Key:**
On the left-hand side, select 'SSH and GPG keys.' Then, click 'New SSH Key' in the upper-right corner. Assign a descriptive name to the key.

**Keep the Window Open:**
Ensure the window remains open while you proceed.

**Copy Public Key:**
Utilize the 'cat' command in the terminal to display the content of your public SSH key file (with a .pub extension).

```
cat ~/.ssh/id_ed25519.pub
```

Copy the output starting from 'ssh-ed25519' to your email address. Return to your GitHub browser window, paste the copied key into the field, keep 'Authentication Key' as the key type, and click 'Add SSH key.' Congratulations! Your SSH key has been successfully added.

### Step 2.5: Testing your key

```
ssh -T git@github.com
```

# Git Basics

## Create Repository

1. Github homepage > |+▾Create new repo|
2. Give repo name + description, add README file > |Create repo|
3. Copy/clone to local machine = |Code| > |SSH| > copy the url
4. Using the command line on local machine, create a new directory for all Odin projects

```
cd ~
mkdir repos
cd repos/
```

5. Clone repo from Github to own computer

```
git clone git@github.com:USER-NAME/REPOSITORY-NAME.git
```

6. To test

```
cd <reponame>
git remote -v
```

## Use the Git workflow

1. Create new file in the git_test folder called “hello_world.txt”

```
touch hello_world.txt
```

2. Check if staged

```
git status
```

> If file is shown in red = not staged

3. Add file to staging area in Git

```
git add hello_world.txt
```

```
git status
```

> If file is green = staged

4. Commit

```
git commit -m "Add hello_world.txt"
git status
```

> Output should say = nothing to commit...

5. Check entry for commit

```
git log
```

## Modify a file

1. Open file in VSC
2. Edit file and Save
3. Open terminal in VSC by pressing <kbd>ctrl</kbd> + <kbd>`</kbd>

```
git status (red = changes not staged)
git add <filename> (add file to staging area)
git status (green = staged)
git add . (add all files to staging area)
git status
git commit -m "Edit README.md and hello_world.txt" (commit all files)
git status (nothing to commit)

git log (see commit history)
git push (or git push origin main)
git status (branch up to date)
```

> Basic git syntax = program | action | destination
