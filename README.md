# Mac Setup
The commands and processes I run to setup a new Mac computer

## Homebrew Setup
```
brew install git
```
```
brew install yarn
```
```
brew install prettier
```
```
brew install python@3.10
```
```
brew install gnupg
```
```
brew install elixir
```
```
brew install --cask phoenix
```
```
brew install --cask google-chrome
```
```
brew install --cask visual-studio-code
```
```
brew install --cask pycharm
```
```
brew install --cask docker
```
```
brew install --cask dotnet
```
```
brew install --cask lastpass
```
```
brew install --cask slack
```
```
brew install --cask postman
```
```
brew install --cask notion
```
```
brew install --cask zoom
```
```
brew install --cask microsoft-outlook
```
```
brew install --cask adobe-acrobat-pro
```
```
brew install --cask raycast
```
```
brew install --cask fig
```
```
brew install --cask figma
```
```
brew install --cask miro
```
```
brew install --cask canva
```
```
brew install --cask robo-3t
```
```
brew install --cask rocket
```

## Node
Download Node Version Manager (NVM) to download and manage Node versions.
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
```

Once that installs, run the following command:
```
nvm install stable
```

## Bash
Create and open bash profile
```
touch ~/.bash_profile
```
```
open -a TextEdit.app ~/.bash_profile
```

Head over to wherever you save your custom config and copy it into TextEdit and save.

## Git
```
git config --global user.name "Matt Sichterman"
```
```
git config --global user.email msichterman1@gmail.com
```

### Configure GPG Commit Signing
1. Log into [GitHub](github.com)
2. Click on your setting under your profile in the top right corner.
![image](https://user-images.githubusercontent.com/38794918/154547859-493d19fc-4aa3-430b-91d3-37fa15de4b74.png)
4. Find your GitHub email address in your Account Settings under the Emails menu option.
    * If it is private this will be someone@user.noreply.github.com.
    * If your email is verified, it will have a green Primary next to your email address and skip to step 5.
5. If your email it is not verified follow [THESE](https://docs.github.com/en/get-started/signing-up-for-github/verifying-your-email-address) steps from Github, then return to these instructions when complete.
6. Open Terminal
7. In Terminal, run:
```
brew install gnupg
```
This and the following step may take a little while, e.g. 15 minutes. Go grab yourself a coffee.

7. In Terminal, run:
```
gpg --version
```
to validate your installation. Your validation should look like (or newer):
![image](https://user-images.githubusercontent.com/38794918/154548080-c3f89fb2-8bdf-4ead-9cfd-1c38ea448903.png)

8. In Terminal, run the following to generate a GPG key pair:
```
gpg --full-generate-key
```

9. At the prompt, specify option 4, "RSA (sign only), and press Enter.

10. At the prompt, specify 4096 as the key size, press Enter.

11. At the prompt, specify 1y as the the length of time the key should be valid, press Enter.


At the prompt, press Enter to leave the comment blank.
Verify that your selections are correct.

Enter your user ID information, which should be your real name (ie FirstName LastName).

Enter your Hudl email address that is verified in Github.
Enter a new passphrase. Keep your secret key secret.
Keep both the key and your password in a secure location (e.g. a password manager), and don't lose it.
Open Finder and navigate to {location} and check to see if you have a gpg.conf file
If the file does not exist, create it using a text editor and renaming the file with a .conf
Add the following two lines to your ~/.gnupg/gpg.conf file.

~/.gnupg/gpg.conf
no-tty
use-agent
Add the public GPG key to your GitHub account https://docs.github.com/en/github/authenticating-to-github/adding-a-new-gpg-key-to-your-github-account
Note: Go through steps 11-14 in "generated your GPG key" (noted in step 4 of the guide above) to generate the actual key
Follow the steps in this guide https://docs.github.com/en/github/authenticating-to-github/telling-git-about-your-signing-key
In Terminal, run git config --global commit.gpgsign true to instruct git to sign all of your commits automatically.
Go to this page and scroll down to 'Method 2 - GPG Suite' and follow the instructions https://github.com/pstadler/keybase-gpg-github#optional-in-case-youre-prompted-to-enter-the-password-every-time
The last step, where you modify ~/.gnupg/gpg-agent.conf should not be necessary. You can cat this file to confirm it has the right contents, though.
It may be desirable to increase the time your password is remembered in the preferences window. 86400 is recommended as this is the number of seconds in a 24 hour period.
Update your environment (Terminal) 

nano ~/.bash_profile
And then Add the following line

GPG_TTY=$(tty)
export GPG_TTY
And then exit out of the editor (^X) and save the document (Y)



And run this command:

source ~/.bash_profile
Note: If you have issues inserting the two like into .bash_profile using nano, insert the two lines manually

Run: gpgconf --kill gpg-agent
Create ssh key by following the steps:
Run: ssh-keygen -t ed25519 -C "<your email>"
press return when asked "Enter file in which to save the key"
press return when asked "Enter passphrase" and "Enter same passphrase again"
Run: ls ~/.ssh
confirm id_ed25519.pub is present
Run: pbcopy < id_ed25519.pub
copies the file into clipboard
Add the SSH key into Github
Navigate to SSH and GPG tab in Github (you can refer to step 16 to find the tab)
Select "New SSH key"
Paste the SSH key (pressing Command+v should work as you copied the key into clipboard in previous step)
Configure SSO → Authorize
Restart your IDE (e.g. Pycharm, VS Code, etc.)
If you try to commit via IDE, it may fail until you have entered your password.
Commit via command line, (e.g. commit -m 'whatever message for your commit')
This should prompt you to enter your password. After this your IDE integration should work, and future command line commits should not prompt you for your password.
Make sure your terminal is not small when committing. If your terminal is too small you cannot be prompted for your password and the signing will fail without giving a helpful error message.
Commit and push to GitHub - you should see a green Verified next to the commit with your GPG Key ID below.




