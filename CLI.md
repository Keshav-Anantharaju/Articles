# Command Line interface

Command Line Interface (CLI) is a text-based interface used to interact with a computer operating system or software by typing commands into a terminal or command prompt.   
Here are some key aspects of a CLI:
### 1) Text based
CLI operates entirely through text commands entered by the user. It doesn't have a graphical interface like a [GUI (Graphical User Interface)](https://en.wikipedia.org/wiki/Graphical_user_interface).
### 2) Shell or Terminal
Users interact with a CLI through a shell (Unix-like systems) or command prompt (Windows). Examples include [Bash](https://en.wiktionary.org/wiki/Bash), [PowerShell](https://en.wikipedia.org/wiki/PowerShell), [Command Prompt](https://en.wikipedia.org/wiki/Cmd.exe), and Terminal.
### 3) Commands and Arguments
Commands are specific instructions to perform tasks such as file manipulation (ls, cd, mkdir), process management (ps, kill), and software management (git, npm, docker). Commands can be followed by arguments or options to modify their behavior.
### 4)Scripting
CLI allows users to automate tasks using shell scripts or batch files, combining multiple commands into a script file for repeated use.
### 5)Flexibility and Power
CLI often provides more granular control over system resources, configuration, and software compared to GUIs. It's favored by developers, system administrators, and power users for its efficiency and scripting capabilities.

## Basic Commands of CLI:
### Fundamentals
#### **1) man**
'man' command is used to display the manual pages (also known as man pages) for various commands and utilities. These manual pages provide detailed information about the command's syntax, options, usage, and examples.

**Basic Usage**
- **Basic Command:**
    ```
    man command
    ```
    Example:
    ```
    man ls
    ```
    This will display the manual page for the 'ls' command, detailing its options, usage, and examples.
- **Navigating and Searching:**
    - Scroll through the manual page using arrow keys or Page Up/Page Down.
    - Search for specific terms within the manual page by typing / followed by the term and pressing Enter.

- **Viewing Sections:**
    - Some commands have multiple sections in their manual pages. For example, man 2 open might refer to a system call open, while man 1 open refers to the open command-line utility.

**Advanced Usage**
- **Update Man Pages:**
    Periodically update the local copy of 'man' pages for latest documentation.

    ```
    sudo mandb
    ```
#### **2) history**
**Basic Usage**
- **Terminal History:**
Use the 'history' command to display a list of previously executed commands in the current session.
    ```
    history
    ```

#### **3) exit**
The exit command is used to close the current terminal session or shell session. 
- **Closing the Terminal Session:** o close the terminal session, simply type
    ```
    exit
    ```


#### **4) alias**
Aliases allow defining shortcuts or alternative names for longer commands or commands with arguments that are use frequently.

**Define an alias:**  
- Open or create '~/.bash_profile' if it doesn't already exist

    ```
    nano ~/.bash_profile
    ```
    For zsh users
    ```
    nano ~/.zshrc
    ```
- Define an alias
    ```
    alias <alias_name>='<command>'
    ```
    Example:
    ```
    alias ll='ls -l'
    ```
- Save and close the file ('Ctrl + X', then 'Y' to confirm, and 'Enter' to save changes if using Nano).
- Source the '.bash_profile' to apply the changes to current session.
    ```
    source ~/.bash_profile
    ```
    For zsh users
    ```
    source ~/.zshrc
    ```
- Alternatively, close and reopen Terminal session to apply the changes.
- To remove an alias temporarily from current session, use 'unalias' followed by the alias name
    ```
    unalias <alias_name>
    ```

#### **5) sudo**
The 'sudo' command stands for "superuser do" and allows a permitted user to execute a command as the superuser or another user, as specified by the security policy configured on the system.
- **Executing Commands:**
To run a command with elevated privileges (as the superuser or root), prepend sudo to the command that is executed. 
    ```
    sudo command
    ```
    Example:
    ```
    sudo brew update
    ```
    You will be prompted to enter your password (the user's password who has sudo privileges) to confirm your identity before the command executes.
- **Running a Command as Another User:**
    'sudo' can also be used to execute a command as another user, if permitted by the system's 'sudoers' file and policies. This is done by specifying the '-u' option followed by the username.
    ```
    sudo -u username command
    ```
- **Installing Software:**
If administrative privileges are needed to install software, use sudo with the installer command.
    ```
    sudo brew install package_name
    ```
- **Managing Services:** Starting or stopping system services often requires sudo, such as:

    ```
    sudo systemctl start service_name
    ```

#### **6) open**
The 'open' command is a versatile utility that allows opening files, directories, applications, and URLs using the default application or a specific one.

**Basic Usage**
- **Opening Files and Directories:**
To open a file or a directory in macOS Finder, simply use the open command followed by the path to the file or directory.
    ```
    open ~/Documents/example.txt
    ```
    Example:
    ```
    open ~/Pictures
    ```
    This will open the 'Pictures' directory in Finder.
- **Opening URLs:**
It can also be used to open URLs in the default web browser.
    ```
    open https://www.example.com
    ```
- **Opening Applications:** To open an application with open, Specify the application name or the full path to the application.
    ```
    open -a "Safari"
    ```
- **Opening with a Specific Application:**
Specify a specific application to open a file or URL by using the '-a' option followed by the application name.
    ```
    open -a "Preview" ~/Documents/image.jpg
    ```
- **Opening Multiple Files:**
Open multiple files at once by listing them after the 'open' command
    ```
    open file1.txt file2.txt file3.txt
    ```

- **Opening Directories in Terminal:** To open the current directory in 'Finder' from the 'Terminal'.
    ```
    open .
    ```
    This will open the current directory in 'Finder'.
#### **7) pipeoperator**
The pipe operator ('|') is a fundamental feature of the command line interface (CLI). It allows to chain multiple commands together, where the output (stdout) of one command becomes the input (stdin) of the next command in the chain.

- **Simple Command Chains:**
To use the pipe operator to pass the output of one command as input to another command.

    ```
    command1 | command2
    ```
    Example:
    ```
    ls -l | wc -l
    ```
- **Filtering Output:**
    ```
    ps aux | grep "chrome"
    ```
    This command lists all running processes ('ps aux') and pipes the output to grep "chrome", which filters ('grep') for lines containing the word "chrome".

### Input/Output Redirection
#### **1) echo**
The 'echo' command in macOS (and in Unix-like systems in general) is used to display a line of text or a string of characters on the standard output (usually the terminal). It's a fundamental command often used in shell scripts and interactive terminal sessions for printing messages, variable values, and other textual information.

**Basic Usage**    
- **The basic syntax of 'echo':**
    ```
    echo [options] [text or variables]
    ```
- **Print a String:**
    ```
    echo "Hello, World!"
    ```
    This will output 'Hello, World!' to the terminal.
- **Print Multiple Strings:**
    ```
    echo "Hello," "World!"
    ```
    This will output 'Hello, World!' with a space between 'Hello,' and 'World!'.

- **Print with Escape Characters:**
    ```
    echo "This is a new line.\nThis is another line."
    ```
    Output:
    ```
    This is a new line.
    This is another line.
    ```
- **Suppress trailing new line:**
    ```
    echo -n "Hello, "
    echo "World!"
    ```
    **-n:** Suppresses the trailing newline, which is automatically appended by default.
- **Using variables:**
    Use echo to display the value of variables:
    ```
    name="Alice"
    echo "Hello, $name!"
    ```
    Output:
    ```
    Hello, Alice!
    ```

#### **2) cat**
The 'cat' command primary function is to concatenate and display the content of files.
**BasicUsage**
- **Displaying File Contents:**
    ```
    cat filename
    ```
    This command will output the entire contents of filename to the terminal.

- **Concatenating Multiple Files:**
    ```
    cat file1 file2
    ```
    This command will display the contents of 'file1' followed by 'file2'. Concatenate multiple files by listing them one after the other.
- **Appending to a File:**
    ```
    cat >> filename
    ```
    After running this command, any text you type will be appended to 'filename'. Press 'Ctrl + D' to exit and save changes.
**Additional Usage:**
- **Numbering Non-blank Lines ('-b'):**
    ```
    cat -b filename
    ```
    This option numbers non-blank output lines.
- **Displaying Line Numbers :**
    ```
    cat -n filename
    ```
- **Creating a New File:**
    ```
    cat > newfile
    ```
    This will create a new file newfile and enter text directly into it. Press 'Ctrl + D' to save and exit.

#### **3) head**
The 'head' command is used to display the beginning lines of a file or files.
**Basic Usage**
- **Displaying First Few Lines:**
    ```
    head filename
    ```
    This command displays the first 10 lines of 'filename' by default. To display different number of lines, specify it with the '-n' option:
    ```
    head -n 20 filename
    ```

- **Displaying Multiple Files:**
    ```
    head file1 file2
    ```

    This command displays the first 10 lines of 'file1', followed by the first 10 lines of 'file2'. Concatenate multiple files by listing them one after the other.
**Advanced Usage**
- **Numbering All Lines:**
    ```
    head -n 15 filename
    ```
    This option displays the first 15 lines of 'filename'. Replace '15' with the number of lines required to display.

- **Displaying Only a Certain Number of Bytes:**
    ```
    head -c 100 filename
    ```
    This option displays the first 100 bytes of 'filename'.




#### **4) tail**
'tail' command is used to display the last few lines of one or more files. It's particularly useful for viewing the end of log files, monitoring changes in real-time with the -f option, or just quickly checking the last few lines of a file.
**Basic Usage**
- **Displaying Last Few Lines:**

    ```
    tail filename
    ```
    This command displays the last 10 lines of 'filename' by default. 
- **To display set of lines:**

    If you want to display a different number of lines, you can specify it with the '-n' option
    ```
    tail -n 20 filename
    ```
- **Displaying Multiple Files:**
    ```
    tail file1 file2
    ```
**Advanced Usage**
- **Follow:**
    ```
    tail -f filename
    ```
    This option allows you to continuously monitor a file for new lines. It's useful for watching log files as they are updated in real-time. To exit from 'tail -f', press 'Ctrl + C'.

- **Numbering All Lines:**
    ```
    tail -n 15 filename
    ```
    This option displays the last 15 lines of 'filename'. Replace '15' with the number of lines you want to display.
- **Displaying Only a Certain Number of Bytes (-c):**
    ```
    tail -c 100 filename
    ```

### Navigating directories
#### **1) mkdir**
The 'mkdir' command is used to create directories (folders) within the file system.

**Basic Usage**
- **Creating Directory**
    To create a directory, simply use the 'mkdir' command followed by the name of the directory you want to create.
    ```
    mkdir directory_name
    ```
    Example:
    ```
    mkdir folder
    ```
    This will create a directory name folder

- **Create Nested Directories:**
    ```
    mkdir -p path/to/nested/directory
    ```
    The '-p' option allows you to create nested directories. If any of the parent directories ('path/to/nested') do not exist, they will be created along with the final directory specified ('directory').

- **Set permission mode:**
    **-m:** Set permissions (mode) for the directory being created. This option is less commonly used in basic scenarios.
    ```
    mkdir -m 755 my_folder
    ```

- **Multiple Directory:**
    ```
    mkdir folder1 folder2 folder3
    ```
- **Relative vs Absolute Paths:**
    
    Directories can be created using both relative and absolute paths. Relative paths are based on the current directory, while absolute paths start from the root directory ('/').

#### **2) cd**
The 'cd' command is used to change the current working directory in the terminal.

**Basic Usage**
- **Change to a Directory:**
    ```
    cd path/to/directory
    ```
    Replace path/to/directory with the actual path of the directory you want to navigate to.

    Example:
    ```
    cd Documents
    ```
    This command changes the current directory to 'Documents' in the user's home directory.
- **Change to Home Directory:**
    ```
    cd
    ```
    Or
    ```
    cd ~
    ```

- **Change to Parent Directory:**
    ```
    cd ..
    ```
- **Tab Completion:**

    Use tab completion to quickly navigate directories and complete file or directory names. For instance, typing 'cd Doc' and then pressing Tab would complete it to 'cd Documents/.'
    ```
    cd ~/Documents
    ```
- **Previous Directory:** 

    Use a hyphen ('-') to quickly switch back to the previous directory you were in
    ```
    cd -
    ```
#### **3) pwd**
The 'pwd' command stands for "print working directory." It is used to display the current directory path (the directory you are currently in) in the terminal.

**Basic Usage**
```
pwd
```
When you press Enter, the command will output the absolute path of the current working directory.
```
$ pwd
/Users/your_username
```
#### **4) ls**
The 'ls' command is used to list directory contents. It displays a list of files and directories in the current directory by default, or in a specified directory if provided.
**Basic Usage**
- **List Contents of Current Directory:**
    ```
    ls
    ```
    This command lists the files and directories in the current working directory.
- **List Contents of a Specific Directory:**
    ```
    ls /path/to/directory
    ```
    Replace '/path/to/directory' with the path to the directory whose contents you want to list. 

    Example
    ```
    ls /Users/username/Documents
    ```
- **Long Format:** This option lists files and directories in long format, including permissions, owner, group, size, and modification date/time.
    ```
    ls -l
    ```
    
- **Show Hidden Files:**
This option lists all files, including hidden files and directories (those starting with '.').
    ```
    ls -a
    ```
    
- **List in Reverse:**
    This option lists files and directories in reverse order.
    ```
    ls -r
    ```
- **Human Readable Sizes:** This option lists file sizes in a human-readable format (e.g., KB, MB, GB).
    ```
    ls -lh
    ```
- **Sort by Modification Time:**
This option lists files sorted by modification time, with the newest first.
    ```
    ls -lt
    ```

#### **5) rmdir**
The 'rmdir' command is used to remove ('delete') empty directories from the filesystem.
**Basic Usage**
- **Remove an Empty Directory:**
    ```
    rmdir directory_name
    ```
- **Remove Parent Directory**
    ```
    rmdir -p path/to/directory
    ```

#### **6) chmod**
The 'chmod' command is used to change the permissions (mode) of files and directories.

**Basic Usage**
- **Changing Permissions Numerically:**
    ```
    chmod 755 filename
    ```
    This command sets the permissions of filename to 'rwxr-xr-x'. The numeric values correspond to permissions
    
    - **1:** Execute permision
    - **2:** Write permision
    - **3:** Write & Execute permision
    - **4:** Read permision
    - **5:** Read & Execute permision
    - **6:** Write & Read permision
    - **2:** Write, Read and Execute permision
- **Changing Permissions Symbolically:**
    ```
    chmod u+w filename
    ```
    This command adds write ('+w') permission for the owner ('u') of filename. Other symbols include 'g' for group, 'o' for others, 'a' for all (equivalent to 'ugo').
    - **u:** user
    - **g:** group
    - **o:** other
    - **+:** Add permision
    - **-:** Deny permision
    - **=:** Overide any permission
- **Recursive:**
    This option changes the permissions recursively for all files and directories within directory.
    ```
    chmod -R 755 directory
    ```

- **Symbolic Mode:**
    ```
    chmod u+x,g+w filename
    ```
    This command adds execute ('+x') permission for the owner ('u') and write ('+w') permission for the group ('g') of filename.


#### **7) chgrp**
The chgrp command is used to change the group ownership of files and directories. 
```
chgrp options group_name file(s)
```
- **Options**
    - **-R:** Recursively change the group ownership of directories and their contents.
    - **-f:** Suppress error messages.
    - **group_name:** The name of the group to which you want to change ownership.
    - **file(s):** The file or files for which you want to change the group ownership.

- **Change Group of a Single File:** 
    ```
    chgrp staff file.txt
    ```
    This command changes the group ownership of 'file.txt' to the 'staff' group.

- **Change Group of Multiple Files:**
    ```
    chgrp admin file1.txt file2.txt
    ```
    This command changes the group ownership of 'file1.txt' and 'file2.txt' to the 'admin' group.

- **Change Group Recursively (Directories and Files):**
    ```
    chgrp -R developers project_directory
    ```
    This command recursively changes the group ownership of 'project_directory' and all its contents (files and subdirectories) to the 'developers' group.

#### **8) chown**
The 'chown' command is used to change the owner and group of files and directories.

**Basic Usage**
- **Changing Owner:**
    ```
    sudo chown newowner filename
    ```
    This command changes the owner of 'filename' to 'newowner'. You typically need to use 'sudo' because changing ownership usually requires superuser privileges.
- **Changing Owner and Group:**
    ```
    sudo chown newowner:newgroup filename
    ```
    This command changes both the owner and group of 'filename' to 'newowner' and 'newgroup', respectively.

- **Recursive:** This option changes the owner and group recursively for all files and directories within 'directory'.
    ```
    sudo chown -R newowner:newgroup directory
    ```

### File manipulation
#### **1) touch**
The 'touch' command is used to create new empty files or update the timestamps (access and modification times) of existing files.

**Basic Usage**
- **Create a New Empty File:**
    ```
    touch filename
    ```
    This command creates a new empty file named filename in the current directory if it does not exist already.

- **Create Multiple Files:**
    ```
    touch file1 file2 file3
    ```
    This command creates multiple empty files ('file1', 'file2','file3') in the current directory.
- **Set Timestamps Explicitly:**
    ```
    touch -t YYYYMMDDHHMM.SS filename
    ```
    This option sets the access and modification times of 'filename' to the specified 'YYYYMMDDHHMM.SS' (year, month, day, hour, minute, second) format.


#### **2) nano**
The 'nano' is a simple and easy-to-use text editor that operates directly in the terminal. It's particularly useful for quick edits of configuration files, scripts, and other text-based documents directly from the command line.

**Basic Usage**

To open a file or create a new file using nano, simply type nano followed by the filename
```
nano filename
```
- **Navigation and Editing**
    - **Navigation:** Use the arrow keys to move the cursor up, down, left, or right within the file.

    - **Editing:** Use the keyboard to type and edit text directly in the file.

    - **Save:** To save the changes made to the file, press Ctrl + O (press Enter to confirm the filename if you're saving for the first time).

    - **Exit:** To exit nano, press Ctrl + X. If there are unsaved changes, nano will prompt you to save them before exiting.
- **Additional Features**

    - **Search and Replace:** Use Ctrl + W to search for text within the file, and Ctrl + \ to search and replace text.

    - **Syntax Highlighting:** nano provides basic syntax highlighting for various file types, making it easier to read and edit code.

    - **Help:** Press Ctrl + G to access the help screen within nano, which provides a list of all available keyboard shortcuts.
- **Creating a New File:**
    ```
    nano newfile.sh
    ```
    This command creates a new file named 'newfile.sh' and opens it in 'nano' for editing.
#### **3) vim**
The 'vim' command is used to launch the Vim text editor from the command line. Vim (Vi IMproved) is a powerful and highly configurable text editor known for its efficiency and extensive feature set.

**Basic Usage**
- **Open an Existing File:**
    ```
    vim filename
    ```
    Replace filename with the name of the file you want to edit.
    
    Example:
    ```
    vim myfile.txt
    ```
- **Create a New File:**
    ```
    vim newfile.txt
    ```
- **Navigation and Editing:**
    - Use arrow keys or 'h', 'j', 'k', 'l' keys for navigation ('left', 'down', 'up', 'right').
    - 'Ctrl + F' for page down, 'Ctrl + B' for page up.
- **Editing:**
    - Press 'i' to enter insert mode (where you can start typing and editing text).
    - Press 'Esc' to exit insert mode and return to command mode.
- **Saving and Exiting:**
    - To save changes and exit Vim, type ':wq' (colon followed by 'wq') and press 'Enter'.
To exit without saving changes, type ':q!' and press 'Enter'.
- **Search and Replace:**
    - Use ':/search_term' to search for search_term within the file, and ':%s/search_term/replace_term/g' to search and replace all occurrences of 'search_term' with 'replace_term'.

- **Help:** 
    - Press ':help' and then 'Enter' to access Vim's built-in help system for more detailed information and commands.

#### **4) less**
The 'less' command is a pager program used to view the contents of a text file one screen at a time. It allows you to navigate through files comfortably, especially when dealing with large files that cannot fit entirely on the screen.

**Basic Usage**
- **View a File:**
    ```
    less filename
    ```
    This command opens 'filename' in the 'less' pager, displaying its contents. You can navigate through the file using various keys (described below).
- **Scrolling:**
    - Use the arrow keys (up/down) or 'j' (down) and 'k' (up) to scroll through the file.
    - You can also use the 'spacebar' to move forward a full screen or 'b' to move backward a full screen.
- **Search:**
    - Press '/' followed by your search term and Enter to search forward.
    - Press '?' followed by your search term and Enter to search backward.
- **Quit:**
    Press 'q' to quit and close less.
- **Other Commands:**

    **'h':** Display help (show all available commands).
    **'G':** Go to the end of the file.
    **'1G' or 'gg':** Go to the beginning of the file.
    **':':** Enter a command (e.g., :n to go to line number n).
#### **5) more**
The 'more' command is used to view the contents of a text file one screen at a time. It is a simple pager utility that allows you to scroll through the file interactively.
**Basic Usage**
- **View content of file:**
    To use 'more' to view the contents of a file, simply type 'more' followed by the filename
    ```
    more myfile.txt
    ```
- **Navigation:**
    - **Spacebar:** Move forward one screen.
    - **Enter:** Move forward one line.
    - **'b':** Move backward one screen.
    - **'q':** Quit 'more' and return to the command prompt.
    - **Scrolling:** 'more' displays one screenful of text at a time. Use the spacebar to advance to the next screen or 'b' to go back if needed.
    - **Searching:** While viewing the file with 'more', you can search for specific text using the '/' command followed by the search term and then pressing 'Enter'.
#### **6) rm**
The 'rm' command is used to remove files and directories from the filesystem.
**Basic Usage:**
- **Remove a File:**
    ```
    rm filename
    ```
    This command deletes 'filename' from the current directory. If 'filename' is a symbolic link, only the link is removed, not the target of the link.

- **Remove Multiple Files:**
    ```
    rm file1 file2 file3
    ```
    This command deletes 'file1', 'file2', and 'file3' from the current directory.
- **Remove Directory and Its Contents Recursively:**
    ```
    rm -r directory
    ```
    Use the '-r' option to recursively remove directory and all its contents, including subdirectories and files.
- **Force Removal:**
    ```
    rm -f filename
    ```
    This option forces the removal of files without prompting for confirmation, even if the file is write-protected or if 'rm' normally wouldn't remove the file.
- **Interactive Removal:**
    ```
    rm -i filename
    ```
    This option prompts for confirmation before removing each file.
- **Verbose Mode:**
    ```
    rm -v filename
    ```
    This option displays detailed information about the files being removed.
#### **7) cp**
The 'cp' command is used to copy files and directories from one location to another. 

**Basic Usage**
- **Syntax:**
    ```
    cp source_file destination_file
    ```
    Example:
    ```
    cp file1.txt /path/to/destination/
    ```
- **Copy a File with a New Name:**
    ```
    cp original.txt newfile.txt
    ```
    This command copies 'original.txt' and renames the copy to 'newfile.txt' in the current directory.

- **Copying Directories and Their Contents**
    To copy directories and their contents recursively, use the '-r' or '-R' option with 'cp'.
    ```
    cp -r source_directory/ destination_directory/
    ```
    Replace 'source_directory' with the name or path of the directory you want to copy, and 'destination_directory' with the name or path of the target location where you want to copy the directory.
- **Prompt Before Overwriting:**
    ```
    cp -i file.txt /path/to/destination/
    ```
    If 'file.txt' already exists in /'path/to/destination/', 'cp' will prompt you to confirm whether you want to overwrite it.


#### **8) mv**
The 'mv' command is used to move or rename files and directories.

**Basic Usage**
- **Move a File:**
    ```
    mv source_file destination_directory
    ```
    This command moves 'source_file' to 'destination_directory'. If 'destination_directory' is a relative path, it is interpreted relative to the current working directory.

- **Rename a File:**
    ```
    mv old_filename new_filename
    ```
    This command renames 'old_filename' to 'new_filename' in the same directory.
- **Move and Rename:**
    ```
    mv source_file new_filename
    ```
    This command moves 'source_file' to 'new_filename', effectively renaming it.
- **Interactive Mode:**
    ```
    mv -i source_file destination_directory
    ```
    This option prompts for confirmation before overwriting existing files in 'destination_directory'.
- **Force Move:**
    ```
    mv -f source_file destination_directory
    ```
    This option forces the move, overriding any warnings or prompts.



### Text processing
#### **1) find** 
'find' command is used to search for files and directories within a specified directory hierarchy based on various criteria such as filename, size, modification time, and more.

**Basic Usage**
- **Find Files by Name:** To search for files by name within the current directory and its subdirectories:

    ```
    find . -name "filename.txt"
    ```
- **Find Directories:** To find directories instead of files:
    ```
    find . -type d -name "directory_name"
    ```
- **Find Files by Type and Name:** To find all files with a specific extension:
    ```
    find . -type f -name "*.txt"
    ```
    
**Advanced option**
- **Find Files by Size:** To find files based on size (e.g., find files larger than 1MB):
    ```
    find . -type f -size +1M
    ```
    Adjust +1M as needed (e.g., +1G for files larger than 1GB).

- **Find Files by Modification Time:** To find files modified within a specific timeframe (e.g., last 7 days):
    ```
    find . -type f -mtime -7
    ```
- **Executing Commands on Found Files:** You can also execute commands on the files found by find. For example, to delete all .tmp files:
    ```
    find . -type f -name "*.tmp" -delete
    ```
- **Example Combining Conditions:** 
    ```
    find . -type f -name "*.log" -mtime -30
    ```

#### **2) sort** 
It's used primarily to sort lines of text alphabetically or numerically, either in ascending or descending order.
    
**Basic Usage**
- **Sorting Lines of Text:** To sort lines of text from standard input (typically output from another command or piped input)

    ```
    sort
    ```
    Example with piped input:
    ```
    echo -e "banana\napple\ncherry" | sort
    ```
    Output:
    ```
    apple
    banana
    cherry
    ```
- **Sorting Files:** To sort the contents of a file and display the sorted output
    ```
    sort filename.txt
    ```
    Example with sorting in reverse order (descending):
    ```
    sort -r filename.txt
    ```
- **Sorting Numerically:** Use '-n' flag to sort numerically instead of alphabetically
    ```
    echo -e "10\n2\n1" | sort -n
    ```
    Output:
    ```
    1
    2
    10
    ```
- **Ignoring Case:** Use '-f' flag to ignore case distinctions
    ```
    echo -e "Apple\nbanana\napple" | sort -f
    ```
    Output:
    ```
    Apple
    apple
    banana
    ```
**Advanced Usage:**
- **Unique Lines Only:** Use '-u' flag to output only unique lines (remove duplicates):
    ```
    echo -e "apple\nbanana\napple" | sort -u
    ```
    Output:
    ```
    apple
    banana
    ```
- **Sorting Based on a Column:** Use '-k' flag to sort based on a specific column (based on specified field and character position):
    ```
    echo -e "John 25\nAlice 30\nBob 20" | sort -k2n
    ```
    Output:
    ```
    Bob 20
    John 25
    Alice 30
    ```
- **Sorting with Custom Delimiters:** Use '-t' flag to specify a custom delimiter (e.g., comma):
    ```
    echo -e "John,25\nAlice,30\nBob,20" | sort -t',' -k2n
    ```
    Output (sorted by age):
    ```
    Bob,20
    John,25
    Alice,30
    ```
#### **3) grep** 
'grep' command is used to search for patterns within files or output. It's a powerful tool for text matching and filtering.

**Basic Usage**
- **Search for a Pattern in a File:** To search for occurrences of a pattern (text or regular expression) within a file:
    ```
    grep "pattern" filename
    ```
- **Search in Multiple Files** You can search for a pattern in multiple files by specifying them after the pattern:
    ```
    grep "pattern" file1.txt file2.txt
    ```
- **Search Recursively in Directories** To search for a pattern recursively in all files within a directory and its subdirectories:
    ```
    grep -r "pattern" directory
    ```
**Advanced Usage**
- **Case-Insensitive Search:** To perform a case-insensitive search (ignore case):
    ```
    grep -i "pattern" filename
    ```
- **Counting Matches:** To count the number of occurrences of a pattern:
    ```
    grep -c "pattern" filename
    ```

- **Display Matching Lines:** To display only the lines that match the pattern:
    ```
    grep -n "pattern" filename
    ```
    '-n' option displays line numbers along with matching lines.
- **Display Matching Files:** To display only the files that contain the pattern
    ```
    grep -l 'pattern' *
    ```
    Will match all the files in current directory
    ```
    grep -l -r 'pattern' .
    ```
    Will match all the files in sub directory
- **Inverse or Negative Match:** To display lines that do not match a pattern:
    ```   
    grep -v "pattern" filename
    ```
    For multiple patterns
    ```
    grep -v -e 'pattern1' -e 'pattern'filename
    ```
    Or
    ```
    grep -v -E 'pattern1|pattern2|pattern3' filename
    ```
- **Regular Expression Support:** For example, to match lines starting with "abc":
    ```
    grep "^abc" filename
    ```
- **Recursive Search with Line Numbers:** To perform a recursive search and display line numbers for matches:
    ```
    grep -rn "pattern" directory
    ```
**Multiflag example**
```
grep -rn "error" ~/logs/*.log
```
Will search for "error" in all '.log' files within the '~/logs' directory, displaying matching lines with line numbers

#### **4) wc** 
'wc' command is a utility used in the Terminal to count words, lines, characters, and bytes in files or standard input.

**Basic Usage**
- **Counting Lines:** To count the number of lines in a file or from standard input:
    ```
    wc -l filename.txt
    ```
    Output:
    ```
    42 filename.txt
    ```
    This shows that 'filename.txt' has 42 lines.

- **Counting Words:** To count the number of words in a file or from standard input:
    ```
    wc -w filename.txt
    ```
    Output:
    ```
    512 filename.txt
    ```
    This indicates that 'filename.txt' contains 512 words.

- **Counting Characters:** To count the number of characters in a file or from standard input (including spaces, tabs, and newline characters)
    ```
    wc -c filename.txt
    ```
    Output:
    ```
    2314 filename.txt
    ```
**Advanced useage**
- **Displaying Multiple Counts:** To display all counts (lines, words, characters) in a single output for a file or from standard input:
    ```
    wc filename.txt
    ```
    Output:
    ```
        42    512   2314 filename.txt
    ```
    Here, '42' represents the number of lines, '512' is the number of words, and '2314' is the number of characters in 'filename.txt'.

- **Counting Output of Commands:** You can use 'wc' with the output of other commands by using a pipe ('|')
    ```
    echo "Hello, world!" | wc -c
    ```
    Output:
    ```
    14
    ```
    This counts the number of characters in the output of 'echo "Hello, world!"', including the newline character.

#### **5) sed** 
The 'sed' command (stream editor) is used for text processing and manipulation. It allows you to perform operations such as search, find and replace, insert, delete, and more on text streams or files.

**Basic Usage**
- **Replace Text in a File:** To replace occurrences of a string (or pattern) with another string in a file
    ```
    sed -i '' 's/pattern/replacement/g' filename
    ```
    **-i '':** Edit files in place. The '' is required on macOS to specify that no backup file should be created. If you omit '', macOS may throw an error.

    **'s/pattern/replacement/g':** Substitution command ('s'). Replace **pattern** with **replacement** globally (g).

    For example, to replace all occurrences of "old" with "new" in 'file.txt'
    ```
    sed -i '' 's/old/new/g' file.txt
    ```
- **Insert or Append Text:** To insert or append text before or after a specific line number
    ```
    sed -i '' '3i\new_line_text' filename
    ```
    This inserts 'new_line_text' before line 3 in 'filename'.

    To append after a specific line number
    ```
    sed -i '' '5a\appended_text' filename
    ```
    This appends 'appended_text' after line 5 in 'filename'.
- **Delete Lines:** To delete lines matching a pattern or line number:
    ```
    sed -i '' '/pattern/d' filename
    ```
    This deletes lines containing 'pattern' in 'filename'.

    To delete a specific line number (e.g., line 4):
    ```
    sed -i '' '4d' filename

    ```
- **Regular Expressions:** 'sed' supports powerful regular expressions for pattern matching and substitution. For example, to replace lines starting with "abc" with "xyz":
    ```
    sed -i '' '/^abc/s/.*/xyz/' filename
    ```

- **Pipe Usage:** 'sed' commands can also be combined with pipes ('|') to process input from other commands. For example, to filter output before displaying:
    ```
    echo "hello world" | sed 's/world/universe/'
    ```
**Example:** 

Replace all occurrences of "apple" with "orange" in 'file.txt' and create a backup file ('file.txt.bak'):
```
sed -i '.bak' 's/apple/orange/g' file.txt
```    

#### **6) date** 
The 'date' command is used in the Terminal to display and manipulate the current date and time.
**Basic Usage:**
- **Displaying Current Date and Time:** To display the current date and time
    ```
    date
    ```
    Output:
    ```
    Thu Jun 25 12:34:56 EDT 2024
    ```
-  **Formatting Date and Time:** You can specify a custom format using the '+' symbol followed by format placeholders:
    ```
    date "+%Y-%m-%d %H:%M:%S"
    ```
    Output:
    ```
    2024-06-25 12:34:56
    ```
    **%Y:** Year (4 digits)

    **%m:** Month (01-12)

    **%d:** Day of the month (01-31)

    **%H:** Hour (00-23)

    **%M:** Minute (00-59)

    **%S:** Second (00-59)

**Manipulating Date and Time:**
- **Setting System Date and Time** (requires root access): To set the system date and time
    ```
    sudo date MMDDHHMMYYYY.ss
    ```
    Replace MMDDHHMMYYYY.ss with the desired date and time in the format Month (MM), Day (DD), Hour (HH), Minute (MM), Year (YYYY), and seconds (ss).
    Example
    ```
    sudo date 062512342024.00
    ```
    This sets the date to June 25th, 2024, 12:34:00 PM.

- **Adjusting Date and Time:** You can adjust the current date and time by specifying a relative time using the '-v' flag
    ```
    date -v +1d
    ```
    This adds 1 day to the current date. You can adjust by days (+1d, -3d), months (+1m, -2m), years (+1y, -1y), hours (+1H, -1H), minutes (+10M, -5M), or combinations thereof.

- **Displaying UTC Time:** To display UTC time
    ```
    date -u
    ```
    Output:
    ```
    Thu Jun 25 16:34:56 UTC 2024
    ```
#### **7) awk**
'awk' command is a powerful tool for text processing and manipulation. It allows you to specify patterns and actions to perform on input data, making it highly versatile for tasks such as extracting specific columns from files, performing calculations, and filtering data based on conditions.

    ```
    awk 'pattern { action }' file
    ```
**Basic Usage**
- **Print specific columns from a file:** 
    ```
    awk '{ print $1, $3 }' file.txt
    ```
    This command prints the first and third columns of each line in file.txt. Columns are separated by whitespace (default delimiter).

- **Filter lines based on a condition:** 
    ```
    awk '$2 > 50 { print $1, $2 }' data.txt
    ```
    This command prints the first and second columns of lines where the second column ($2) is greater than 50 in 'data.txt'.

- **Calculate and print totals:**
    ```
    awk '{ sum += $1 } END { print "Total:", sum }' numbers.txt
    ```
    This command calculates the sum of the numbers in the first column ($1) of numbers.txt and prints the total after processing all lines (END block).
- **$0:** Represents the entire current line.

- **$1, $2, ...:** Represent the first, second, etc., fields (columns) of the current line, based on the field separator (default is whitespace).
- **NF:** Represents the number of fields (columns) in the current line.
- **NR:** Represents the current record (line) number being processed.

### Package management
#### brew
The 'brew' is short for Homebrew, which is a package manager for macOS and is widely used to install and manage software packages.
- **Installing Packages:**
    ```
    brew install <package>
    ```
    This installs the specified package.


- **Updating Homebrew and Packages:**
    ```
    brew update
    ```
    This updates the package lists from the repositories.
    ```
    brew upgrade
    ```
    This upgrades all installed packages to their latest versions.
- **Searching for Packages:**
    ```
    brew search <keyword>
    ```
    Searches for packages matching the specified keyword.
- **Listing Installed Packages:**
    ```
    brew list
    ```
    Lists all installed packages.
- **Removing Packages:**
    ```
    brew uninstall <package>
    ```
    Uninstalls the specified package.
- **Viewing Package Information:**
    ```
    brew info <package>
    ```
    Shows information about the specified package.

### System administration
#### Process management
##### **1) ps**
The 'ps' command is used to display information about currently running processes. It provides a snapshot of processes running on the system, including their process IDs (PIDs), resource usage, CPU/memory consumption, and more.

**Basic Usage**
- **Display All Processes:** To display information about all processes running on the system
    ```
    ps aux
    ```
    **a:** Show processes from all users.
    
    **u:** Display detailed information (user-oriented format).
    
    **x:** Include processes not attached to a terminal.

- **Display Specific Process:** To display information about a specific process by PID (Process ID)
    ```
    ps -p PID
    ```
    Replace 'PID' with the actual process ID
    
**Advanced Usage**
- **Custom Output Format:** To customize the output format using ps:
    ```
    ps -o pid,ppid,user,%cpu,%mem,command
    ```
    **-o:** Specify output format. You can choose from various columns like pid, ppid (parent process ID), user, %cpu (CPU usage), %mem (memory usage), command, etc.

- **Search by Process Name:** To search for processes by name
    ```
    ps -ef | grep "process_name"
    ```
    **-e:** Display all the process, including those without controlling terminal
    **-f:** Verbose output

##### **2) top** 
'top' command is used to display real-time information about system processes and resource usage. It provides a dynamic view of processes currently running on the system, CPU and memory utilization, and other system metrics.
    
**Basic Usage**
- **Display Real-Time Process Information:** Simply running 'top' without any options provides a continuously updating list of processes:
    ```
    top
    ```
    By default, 'top' sorts processes by CPU usage.
- **Sort Processes:** You can sort processes based on different criteria

    ```
    top -o -mem
    ```
    **-o**: Change order
    
    **-mem**: Change order by memory
    
    **-cpu**: Change order by cpu

**Advanced Usage**
- **Specific Refresh Rate:** By default, top updates every few seconds. You can specify a custom refresh rate
    ```
    top -s 5
    ```
    This updates top every 5 seconds.

- **Display Specific Columns:** Customize the columns displayed by 'top':
    ```
    top -stats pid,user,cpu,mem,command
    ```
    This specifies columns to display: PID, user, CPU usage, memory usage, and command.

##### **3) df** 
The 'df' command is used in the Terminal to display disk space usage statistics for mounted file systems.

**Basic Usage**
- **Displaying Disk Space Usage:** To display disk space usage statistics for all mounted file systems
    ```
    df
    ```
    This displays information about each mounted file system including the device name, total blocks, used blocks, available blocks, percentage of disk used (Capacity), inode usage (iused and ifree), percentage of inodes used (%iused), and the mount point (Mounted on).
- **Displaying File System Type:** To include the file system type in the output
    ```
    df -Y
    ```
    This adds the Type column to show the file system type (apfs for APFS, devfs for devices, etc.).

- **To display Specific file type:**
    ```
    df -T args
    ```
    Replace args with specific file type
    
    Example:
    ```
    df -T nonfs
    ```
    (Hint: Use lsvfs to display all file types)
    
**Additional Usage**
- **Human Readable Format:** To display sizes in a more human-readable format (e.g., KB, MB, GB):
    ```
    df -h
    ```
- **Specific File System:** To display information for a specific file system (replace /dev/disk1s5 with your desired file system):
    ```
    df -h /dev/disk1s5
    ```

##### **4) pgrep** 
'pgrep' command is used to search for processes based on their names or other attributes and retrieve their process IDs (PIDs).

**Basic Usage**
- **Search for a Process by Name:** To find the PID of a process by its name (e.g., firefox)
    ```
    pgrep firefox
    ```
    This command returns the PID (process ID) of the firefox process if it is running

    ```
    pgrep -l firefox
    ```
    To display more detailed information about the process, use the -l (long) option

**Advanced Usage**
- **Case Insensitive Search:** To perform a case-insensitive search for a process name
    ```
    pgrep -i firefox
    ```
    This command matches firefox, FireFox, FIREFOX, etc., ignoring case.
- **Search for a Process by User:** To find processes owned by a specific user (e.g., root)
    ```
    pgrep -u root
    ```
    This command lists PIDs of processes owned by the user root.
- **Kill Matching Processes:** To kill processes that match a certain criteria (e.g., process name)
    ```
    pgrep -x firefox | xargs kill
    ```
    **-x:** Looks for exact match
    
    **-o:** Looks for oldest match
        
    **-n:** Looks for newest match

        This command finds all firefox processes and sends a kill signal (SIGTERM) to each of them using xargs.

##### **5) uname** 
'uname' command is used to print system information such as the operating system name, system name, release version, and machine hardware name.

**Basic Usage**
- **Display System Name:** To display the system name (kernel name)
    ```
    uname -s
    ```
    Output:

    ```
    Darwin
    ```
- **Display Node Name:** To display the network node hostname (typically the machine's hostname)
    ```
    uname -n
    ```
- **Display Kernel Release:** To display the kernel release version:
    ```
    uname -r
    ```
- **Display Kernel Version:**
    ```
    uname -v
    ```
- **Display Machine Hardware Name:**
    ```
    uname -m
    ```

##### **6) system_profiler** 
'system_profiler' command is a powerful utility that provides detailed information about various hardware and software components of your Mac system. It's particularly useful for gathering comprehensive system configuration details and diagnosing issues.

**Basic Usage**
- **Displaying Basic System Information:** To display a summary of basic system information
    ```
    system_profiler SPSoftwareDataType
    ```
    This command provides an overview of the macOS version, kernel version, boot volume, computer name, user name, and other relevant system information.

- **Displaying Hardware Information:** To display detailed hardware information
    ```
    system_profiler SPHardwareDataType
    ```
    This command provides detailed hardware information such as the model, CPU type, number of cores, amount of RAM, system firmware version, SMC version, serial number, and hardware UUID.

**Advanced Usage**
- **Listing all Data Types:** To list all available data types that system_profiler can provide information on

    ```
    system_profiler -listDataTypes
    ```
    This command lists all the data types that system_profiler can display, which includes various categories like hardware, software, network, USB devices, and more.
- **Saving Output to a File:** To save the output of system_profiler to a text file for later review or analysis
    ```
    system_profiler SPHardwareDataType > hardware_info.txt
    ```

##### **7) kill** 
The 'kill' command is used to terminate processes. It sends signals to processes, allowing you to gracefully stop them or force them to terminate.

**Basic Usage**
- **Terminate a Process by PID:** To terminate a specific process by its Process ID (PID):
    ```
    kill PID
    ```
- **Forcefully Terminate a Process:** If a process does not respond to the default termination signal (SIGTERM), you can forcefully terminate it using SIGKILL:
    ```
    kill -9 PID
    ```
    Or
    ```
    kill -SIGKILL PID
    ```
- **Specifying a particular signal:** Sending a specific signal instead of default TERM
    ```
    kill -s signalname  process
    ```

- **List all signal name**
    ```
    kill -l
    ```
    1&emsp;&nbsp;&nbsp; HUP (hang up)

    2&emsp;&nbsp;&nbsp; INT (interrupt)

    3&emsp;&nbsp;&nbsp; QUIT (quit)

    6&emsp;&nbsp;&nbsp; ABRT (abort)

    9&emsp;&nbsp;&nbsp; KILL (non-catchable, non-ignorable kill)

    14&emsp;&nbsp;&nbsp;ALRM (alarm clock)

    15&emsp;&nbsp;&nbsp;TERM (software termination signal)

**Advance Usage**
- **Terminate All Processes by Name:**

    ```
    pkill process_name
    ```
##### **8) jobs**
The 'jobs' command is used to display the status of jobs that are running in the background within the current shell session.

- **Viewing Jobs:**
To view the status of jobs running in the current shell session, you can use the 'jobs' command.
    ```
    jobs
    ```
    If there are any background jobs running, jobs will list them along with their job number and status.
- **Job Control Basics:**
    - **Background Jobs:** Jobs started with & at the end of a command run in the background.
        ```
        sleep 10 &
        ```
        This starts a 'sleep' command in the background for 10 seconds.

    - **Foreground and Background Switching:** Bring background job to the foreground or send a foreground job to the background using 'fg' (foreground) and 'bg' (background) commands followed by the job number or '%job_id'.
        ```
        fg %1   
        bg %2
        ```
    - **Killing Jobs:**
    You can terminate a job using the kill command followed by the job number or '%job_id'. 
        ```
        kill %1
        ```

#### Networking
##### **1) ifconfig** 
- **Display or configure network interfaces and IP addresses:**
    To display information about all active network interfaces currently configured on the system.

    ```
    ifconfig
    ```
    Or Use
    ```
    ifconfig -a
    ```
- **For wireless network:**
    ```
    ifconfig en0
    ```
- **For wired network:**
    ```
    ifconfig en1
    ```

##### **2) ipconfig** 
- **To display basic IP configuration information:**

    ```
    ipconfig
    ```
- **To get ip address of network interface:**

    ```
    ipconfig getpacket en0 | grep yiaddr
    ```

- **To get mac address for network interface:**
    ```
    ipconfig getpacket en0 | grep chaddr
    ```

##### **3) ping:** 
ping command is used to test the connectivity between your computer and a remote host using ICMP (Internet Control Message Protocol) echo requests and replies.

- **To ping a remote host or ip-address**
    ```
    ping hostname_or_ip_address
    ```
    Replace 'hostname_or_ip_address' with the actual hostname or IP address you want to ping. 

    For Example
    ```
    ping www.google.com
    ```

**Optional Parameters**

- **-c count:** Specify the number of ICMP echo requests to send (default is unlimited until interrupted).
    ```
    ping -c 4 www.google.com   # Send 4 ICMP echo requests
    ```
- **-i interval:** Specify the interval in seconds between sending each ICMP echo request 
    ```
    ping -i 2 www.google.com   # Send ICMP echo requests every 2 seconds
    ```
- **-t timeout:** Specify the timeout in seconds to wait for each ICMP echo reply.
    ```
    ping -t 5 www.google.com   # Set timeout to 5 seconds
    ```
- **-s packetsize:** Specify the size of ICMP echo packets in bytes 
    ```
    ping -s 100 www.google.com   # Send ICMP echo packets with size 100 bytes
    ```
- **-q: Quiet** output. Only display summary statistics at the end.
    ```
    ping -q www.google.com
    ```

    Here is an example using multiple options with 'ping'

    ```
    ping -c 4 -i 2 -t 5 www.google.com
    ```
    This command sends 4 ICMP echo requests to 'www.google.com', with a 2-second interval between each request, and a timeout of 5 seconds for each reply.
##### **4) ssh** 
The 'ssh' command (Secure Shell) is used to establish secure, encrypted connections to remote servers or devices over a network. It's commonly used for accessing and managing remote systems, transferring files securely, and executing commands on remote hosts. Here are some essential 'ssh' commands and usage examples:

- **To connect to a remote server using SSH:**
    ```
    ssh username@hostname
    ```
    Replace 'username' with your remote username and 'hostname' with the IP address or domain name of the remote server. For example:
    ```
    ssh john@example.com
    ```
- If your SSH server is running on a non-default port (not port 22), specify the port with the -p option:
    ```
    ssh -p port_number username@hostname
    ```
    For example, if your SSH server is running on port 2222:
    ```
    ssh -p 2222 john@example.com
    ```
- **SSH with Key Authentication**

    Using SSH keys for authentication is more secure than password authentication. Here's how you can use SSH with a specific private key file (-i option):
    ```
    ssh -i /path/to/private_key username@hostname
    ```

- **Running Commands on a Remote Server**
    ```
    ssh username@hostname ls -l
    ```
- **Copying Files with 'scp'**

    'scp' (Secure Copy) is used to securely transfer files between local and remote hosts over an SSH connection. Here's how to copy a file from the local machine to a remote server:

    ```
    scp /path/to/local_file username@hostname:/path/to/destination
    ```
    Example
    ```
    scp ~/Documents/file.txt john@example.com:/home/john/
    ```


    




## Advantages of CLI
- **Efficiency:** Experienced users can perform tasks quickly using keyboard shortcuts and commands.

- **Remote Access:** CLI is often used for remote server management via [SSH (Secure Shell)](https://en.wikipedia.org/wiki/Secure_Shell)

- **Scriptability:** Tasks can be automated and repeated using scripts.

- **Resource Efficiency:** CLI typically consumes fewer system resources compared to GUIs.
## Disadvantages of CLI
- **Learning Curve:** Requires learning commands and their syntax.

- **Less Intuitive:** Some tasks are easier to perform using GUIs, especially for new users.

- **Limited Visibility:** Complex operations or data visualization may be more challenging in CLI compared to GUIs.