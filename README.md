# 🚀 Unlimited Storage: Your Gateway to Secure File Management

Welcome to **Unlimited Storage**, a robust solution for secure file upload, encryption, and retrieval. 

## 🧩 Prerequisites

Before we dive in, there are a few things you need to have in place:

1. **Docker**: Install Docker based on your operating system:
   - [Windows Users, Click Here](https://docs.docker.com/desktop/install/windows-install/)
   - [Linux Users, Click Here](https://docs.docker.com/desktop/install/linux-install/)
   - [Mac Users, Click Here](https://docs.docker.com/desktop/install/mac-install/)

2. **Git Repository**: Our treasure chest of code. Clone this repository and navigate into it:
   ```bash
   git clone https://github.com/your-username/unlimited-storage.git
   cd unlimited-storage
   ```

3. **Docker Volume**: This is our persistent storage for the database. Create a docker volume:
    ```bash
    docker create volume file-db
    ```

4. **Create a secure AES key**: Using Python:
    ```bash
    import os
    key = os.urandom(32).hex()
    print(key)
    ```
    
5. **Environment Variables**: Set the following environment variables:

    - `SQL_VOLUME`: This is the name of the volume you created in step 3. In our case, `file-db`.
    - `MYSQL_ROOT_PASSWORD`: This is the root password for MySQL. Keep it secret, keep it safe!
    - `SQL_USER`: This is the username for the Database. For example, `Spectron`.
    - `SQL_DATABASE`: This is the name of your MySQL database. For example, `file_upload`.
    - `DC_CHANNEL`: Your Discord channel awaits! Put your Discord channel ID here.
    - `DC_TOKEN`: Use Discord integration by adding your bot token here.
    - `AES_HEX_KEY`: Your key to the encrypted realm. Enter the AES encryption key in hexadecimal format.
