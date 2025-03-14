# To implement this script, follow these steps and note its dependencies:

# Save and Prepare the Script:

1.  Create a File: for example, create_users.sh.
# Make it Executable: Run:
- chmod +x user_management.sh

2. Run the Script with Proper Privileges:
- Pass the input file path as an argument
Root Privileges: This script must be executed with root or sudo privileges since it creates users and groups, and writes to system directories.

- sudo ./user_management.sh <input_file>

# Input File Format: The input file should contain user details in the format:
    username;group1,group2,group3
Eg.
alice;admin,developers
bob;sales
charlie;    
# In this example:
alice is added to groups admin and developers.
bob is added to the sales group.
charlie has no additional groups specified beyond their personal group.


3. Script Dependencies:

# System Commands:
    bash (the script interpreter)
    groupadd and useradd for creating groups and users.
    usermod for modifying user group membership.
    getent and id for checking if users and groups exist.
    chpasswd for setting user passwords. 

# Utilities:
openssl is used to generate a random password (openssl rand -base64 12).
Standard utilities such as touch, chmod, mkdir, echo, and date commands.

# Directory Permissions:
The script writes to /var/log/user_management.log and /var/secure/user_passwords.csv, so ensure the /var/secure directory exists (the script creates it if it doesn’t) and the executing user (root) has write access to these locations.

# What the Script Does:

- Validates Input: Checks if it’s run as root and verifies that an input file is provided and exists.
- Logs Activity: Creates or updates a log file in /var/log/user_management.log to record actions.

- User and Group Management:
Creates a personal group for the user if it doesn’t exist.
Adds new users with a home directory and assigns them to their personal group.
Adds users to additional groups specified in the input file.

- Password Generation: Uses OpenSSL to generate a random password for each user, applies it via chpasswd, and saves the credentials securely in /var/secure/user_passwords.csv.

By ensuring you have the required utilities installed and running the script with the correct permissions, you can effectively implement and run this script to automate user management tasks on your system.