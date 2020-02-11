# Setting Up Your Git Client

### Prerequisites

#### Ensure `ssh-keygen` is installed  
  * Linux and macOS Users: ssh-keygen should already be installed on your computer  
  * Windows Users: Download and install [the full suite of puTTY utilities](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)  

#### Install a Git client on your development computer
  * Example 1: [Visual Studio Code](https://code.visualstudio.com/download)
  * Example 2: [Cygwin](https://cygwin.com/install.html) (64-bit) on Windows. Command line install string: `setup-x86_64.exe -q --packages="bash,bzip2,curl,git,nano,openssh,qawk,ssh,tar,wget,vim"`) 

### Create an SSH key
1. Open Terminal or Command Prompt and enter the following command string: `ssh-keygen -t rsa -C "username@domain.com" -b 4096`  
2. Save newly created key to file: `/home/username/.ssh/id_rsa`  
3. Enter a passphrase (or leave blank for no passphrase): <current passphrase == current AD domain password>  
4. Identification is saved to `/home/username/.ssh/id_rsa`  
5. Key fingerprint and random art image is shown  

### Copy SSH keys to GitHub Personal Profile
1. Check SSH public key: `cat ~/.ssh/id_rsa.pub`  
2. Copy SSH public key via Command Line: `type id_rsa.pub | clip`  
3. Paste to GitHub SSH keys tab in personal profile

### Personalize Git client
1. List configuration setting: `git config --list`  
2. Set credentials manager to "manager": `git config --global credential.helper manager`
3. Set user name: `git config --global user.name "Patrick Jane"`  
4. Set user e-mail address: `git config --global user.email "PatrickJ@acme.com"`  
5. Set default code editor: `git config --global core.editor "vscode"`  
6. Create alias: `git config --global alias.lr 'log --reverse'`  
7. Set up pager to wrap lines: `git config core.pager 'less -r'`  

### Initialize your local working directory
1. Change to working directory. E.g., `cd /home/username/working/`    
2. While in working directory run the following command `git init`  

### Clone a Repo
Clone your shared network-based code repository by running the command `git clone git@servername.domainname.tld:IT/Operations.git  *`  
