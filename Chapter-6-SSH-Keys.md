SSH KEYS
=
  ### Secure Socket Shell ( SSH ):
  - It is special network protocol leveraging public-key cryptography to enable authorized users to remotely access a computer or other device via access credentials called SSH keys.
  - So, In order to Push any file from ***VSC*** into Github one need to prove Github that they are the owner of that account. 
  - Therefore, they need to connect the local machine to Github account.

  ### Steps to Connect Local Machine to Github
  - Generate the SSH keys local using the command given below
     - Type of encryption -> -t rsa
     - Strength of encryption -> -b 4096  
  ```
  ssh-keygen -t rsa -b 4096 -C "Your_email.com" 
  ```
  - Type of encryption -> -t rsa
  - Strength of encryption -> -b 4096

  -  Enter the file name to save the key.
  -  Enter passphrase or leave it blank.
  -  Your Key is generated.
  -  To know your key give ``` cat [filename].pub ``` command.
  -  Copy the key by just highlighting it or give ``` pcopy < [ file location] ```.
  
  ### Adding SSH Keys to SSH Agent
  - To ensure the ssh-agent is running type the following command.
  ```
  # start the ssh-agent in the background
  $ eval "$(ssh-agent -s)"
  ```
  - This results in 
  ```
  > Agent pid 59566
  ```
  - Add SSH private key to the ssh-agent.
  ```
  $ ssh-add ~/.ssh/id_ed25519
  ```
  - Goto Github hit ***settings*** hit ***SSH and GPG Keys*** hit ***new SSH Keys*** and paste the copied key.
  


  
