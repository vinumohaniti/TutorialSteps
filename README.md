# TutorialSteps
git ssh add and alll

To create and configure an SSH key for Git on Windows, you can use Git Bash (which is installed automatically with Git for Windows). [1, 2] 
## Step 1: Generate the SSH Key

   1. Open the Start Menu, search for Git Bash, and open it. [2] 
   2. Paste the following command into Git Bash (replace the email with your GitHub/GitLab account email):
   
   ssh-keygen -t ed25519 -C "your_email@example.com"
   
   (Note: if your Git server doesn't support the modern ED25519 format, use ssh-keygen -t rsa -b 4096 -C "your_email@example.com" instead). [2, 3, 4] 
   3. Press Enter to accept the default file location (/c/Users/your_username/.ssh/id_ed25519). [5, 6] 
   4. When prompted, type a secure passphrase and press Enter, then type it again to confirm. (You can also press Enter twice to leave it blank, but a passphrase is recommended for security). [2, 4, 7] 

------------------------------
## Step 2: Add the Key to the SSH Agent
To prevent having to type your passphrase every time you communicate with the Git server, add it to the local background agent: [5] 

   1. Start the SSH agent by running:
   
   eval "$(ssh-agent -s)"
   
   2. Add your private key to the agent: [5] 
   
   ssh-add ~/.ssh/id_ed25519
   
   
------------------------------
## Step 3: Copy the Public Key to Your Clipboard
You need to copy the contents of the public key file (the .pub extension) to add it to your Git provider (like GitHub, GitLab, or Bitbucket). [1, 8] 
Run the following command in Git Bash to copy the key text directly to your Windows clipboard:

clip < ~/.ssh/id_ed25519.pub

(Alternatively, you can view the text with cat ~/.ssh/id_ed25519.pub and highlight-copy it manually.)
------------------------------
## Step 4: Add the Key to Your Git Provider
Now, register the key with your hosting service: [2, 8] 

* For GitHub: Go to Settings > SSH and GPG keys > Click [New SSH Key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) > Paste your key into the Key field and give it a title (e.g., "Windows Laptop"). [2, 7] 
* For GitLab: Navigate to Preferences > SSH Keys > Click Add new key > Paste the key and save. [4, 8] 

------------------------------
## Step 5: Test the Connection
To verify that everything works correctly, run one of these commands in Git Bash: [2] 

* For GitHub: ssh -T git@github.com
* For GitLab: ssh -T git@gitlab.com [2] 

