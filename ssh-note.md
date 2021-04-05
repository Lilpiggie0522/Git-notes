# Tutorial Link: https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh
# Connection
To connect to a server via ssh, type the following command:
ssh -p 22 root@THE IP ADDRESS OR HOST NAME
Then enter your password

# SSH setup via github
1. use the following command to generate ssh key:
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

2.when seeing > Enter a file in which to save the key (/Users/you/.ssh/id_ed25519): [Press enter] Press enter to accept default name and location or give it a different name.

3. passphrase can be left blank

4. Go into the folder that your key is contained in by using"

$ cd .ssh
$ ls | grep id_rsa 

##don't know why it does not let me search from the entire system but only within the .ssh if named id_rsa

5. use the following command to print the key on screen:
$ cd .ssh
$ cat id_rsa.pub

6. Then go to github/settings/SSH and GPG keys

7. add key into local git command line interface knows the key using following: 
$ eval "$(ssh-agent -s)"
> Agent pid xxxx

8. check if config file exists 
$ open ~/.ssh/config
> The file /Users/you/.ssh/config does not exist.
If not create using:
$ touch ~/.ssh/config

9. Open config in .ssh write: 
> replacing ~/.ssh/id_ed25519 if you are not using the default location and name for your id_ed25519 key.



Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_ed25519
  
into the file.

10. Add your ssh private key to the ssh-agent, 
> If you created your key with a different name, or if you are adding an existing key that has a different name, replace id_ed25519 in the command with the name of your private key file

using the following command:
$ ssh-add -K ~/.ssh/id_ed25519
























