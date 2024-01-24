# 🚀 Unlimited Storage: Your Gateway to Secure File Management

Welcome to **Unlimited Storage**, a robust solution for secure file upload, encryption, and retrieval. 

## 🧩 Prerequisites

Before we dive in, there are a few things you need to have in place:

1. **Docker**: Install Docker based on your operating system:
   - [Windows Users](https://docs.docker.com/desktop/install/windows-install/)
   - [Linux Users](https://docs.docker.com/desktop/install/linux-install/)
   - [Mac Users](https://docs.docker.com/desktop/install/mac-install/)
   
2. **Git**: Install Git based on your operating system:
    - [Windows Users](https://git-scm.com/download/win)
   - [Linux Users](https://git-scm.com/download/linux)
   - [Mac Users](https://git-scm.com/download/mac)

3. **Verify installations**: Verify Docker and Git beeing installed correctly:

    (If you are on Windows and didn't restart your pc yet, do it now.)
   
    - Open up your terminal and type:
      ```bash
      docker --version
      ```
      It should now show the version of your Docker installation.

    - Next, type:
      ```bash
      git --version 
      ```
      If installed correctly, it should now show the corresponding version of your Git.
    

4. **Discord**: Create a Bot and select a channel:
    - Go to your [Discord Developer Portal](https://discord.com/developers/applications) and create a new application. In the **Bot** page, click on *"Reset Token"* and save your new Token somewhere safe.
   
    - In the *Privileged Gateway Intents* section of the **Bot** page, enable all 3 Features:
        - PRESENCE INTENT
        - SERVER MEMBERS INTENT
        - MESSAGE CONTENT INTENT
        
    - In the **OAuth2 URL Generator** page, click on the *"Bot"* checkbox in the *SCOPES* list. A new *BOT PERMISSIONS* list should appear below. Select the *"Administrator"* checkbox in the new list.

    - Now scroll down to the newly Generated url and copy it.

    - Create a new Discord Server and paste the previously generated link in any text-channel. Afterwards, click in the link and invite your new Discord bot to your new Server. The bot should now appear in the members section to the right.

    - Copy the desired channel's ID by right-clicking your desired channel on the left. Save that ID for later.



##  ⚙ Setup

To Setup your application, follow these simple steps:

1. **Git Repository**: Clone this repository and navigate into it:
   ```bash
   git clone https://github.com/your-username/unlimited-storage.git
   
   cd unlimited-storage
   ```

2. **Docker Volume**: This is our persistent storage for the database. Create a docker volume:
    ```bash
    docker create volume file-db
    ```

3. **Create a secure HEX-AES key** using Python:
    ```python
    import os
    key = os.urandom(32).hex()
    print(key)
    ```
    
4. **Environment Variables**: Set the following environment variables in the **.env** file:

    - `SQL_VOLUME`: This is the name of the volume you created in **step 3**. In our case, `file-db`.
    - `MYSQL_ROOT_PASSWORD`: This is the root password for MySQL. Keep it secret, keep it safe!
    - `SQL_USER`: This is the username for the Database. For example, `Spectron`.
    - `SQL_DATABASE`: This is the name of your MySQL database. You should leave it at `file_upload` for now.
    - `DC_CHANNEL`: Your Discord channel awaits! Put your Discord channel ID here.
    - `DC_TOKEN`: Use Discord integration by adding your bot token that you saved earlier here.
    - `AES_HEX_KEY`: Your key for the file encryption. Enter the AES encryption key in hexadecimal format that you created in **step 4**.


# 🏁 Run the application:

If you carefully followed the previous steps, you are now ready to run the application:

1. Navigate to the unlimited-storage in your Terminal if you haven't already and type:
      ```bash
      docker-compose up -d
      ```
      It should now start downloading MySQL aswell as the unlimited-storage repo automatically and execute it automatically.

2. Verify the success by running:
      ```bash
      docker ps
      ```
      If everything done right, you should now see two containers running:
          - docker-db-1
          - docker-app-1

3. 🥳 Congrats!
        You can now visit your application in the browser, by opening:

    - _http://127.0.0.1:5005/upload_ for upload

    - _http://127.0.0.1:5005/retrieve_ for retrieving using the ID given after the upload
