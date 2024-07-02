# User Creation Script

This script automates the process of creating users on a Linux system. It reads a specified file containing usernames and their associated groups, creates users with those names, assigns them to the specified groups, generates random passwords for each, and logs the actions taken.

## Features

- **User Creation**: Automatically creates users with home directories.
- **Group Assignment**: Adds users to specified groups.
- **Random Password Generation**: Generates secure random passwords for each user.
- **Logging**: Logs all actions to a log file and saves user passwords securely.

## Prerequisites

- A Linux system with `bash`, `useradd`, `chpasswd`, and `openssl` installed.
- Root or sudo privileges for creating users and writing to log and password files.

## Usage

1. Prepare a text file (`users.txt`) with usernames and their associated groups, separated by a semicolon (`;`). Each user and their groups should be on a new line. For example:

    ```
    johndoe;sudo,dev,www-data
    janedoe;www-data
    ```

2. Run the script with the text file as an argument:

    ```bash
    sudo bash create_users.sh users.txt
    ```

3. Check the log file at `/var/log/user_management.log` for details of the actions taken.

4. Access generated passwords in the secure file `/var/secure/user_passwords.csv`. This file is only readable by root.

## Security Notes

- The script sets the permissions of the password file to `600` to restrict access to root.
- Home directories are set with permissions to ensure only the user and root have access.

## Log File

The log file `/var/log/user_management.log` contains details of the user creation process, including any errors or notifications about existing users.

## Password File

The password file `/var/secure/user_passwords.csv` contains the usernames and their generated passwords in CSV format. Handle this file with care and ensure it is securely stored.

## Customization

You can modify the script to change the default shell, home directory location, or password complexity by editing the `useradd` and `openssl` commands within the script.

## License

This script is provided "as is", without warranty of any kind. Use at your own risk.