# Linux Commands

#### **Process & Port Management**

1.  **Find which app is using a port**:

    ```bash
    sudo lsof -i :PORT_NUMBER
    ```

    Example:

    ```bash
    sudo lsof -i :8080
    ```
2.  **Kill an app using a port**:

    ```bash
    sudo kill -9 $(sudo lsof -t -i :PORT_NUMBER)
    ```
3.  **List all running processes**:

    ```bash
    ps aux
    ```
4.  **Kill a process by PID**:

    ```bash
    kill -9 PID
    ```

#### **File Operations (Read, Write, etc.)**

1.  **View contents of a file**:

    ```bash
    cat file.txt
    ```

    or

    ```bash
    less file.txt
    ```
2.  **Write to a file**:

    ```bash
    echo "text" > file.txt
    ```
3.  **Append to a file**:

    ```bash
    echo "text" >> file.txt
    ```
4.  **Copy a file**:

    ```bash
    cp source_file destination_file
    ```
5.  **Move (or rename) a file**:

    ```bash
    mv source_file destination_file
    ```
6.  **Remove a file**:

    ```bash
    rm file.txt
    ```

#### **File Search**

1.  **Find a file by name**:

    ```bash
    find /path -name "filename"
    ```
2.  **Search inside files for a string**:

    ```bash
    grep -r "text_to_search" /path/to/search
    ```

#### **Networking**

1.  **Check IP address**:

    ```bash
    ip addr show
    ```

    or

    ```bash
    ifconfig
    ```
2.  **Ping a host**:

    ```bash
    ping example.com
    ```
3.  **Display routing table**:

    ```bash
    netstat -rn
    ```

#### **Service & Systemd Commands**

1.  **Check status of a service**:

    ```bash
    sudo systemctl status service_name
    ```
2.  **Start a service**:

    ```bash
    sudo systemctl start service_name
    ```
3.  **Stop a service**:

    ```bash
    sudo systemctl stop service_name
    ```
4.  **Restart a service**:

    ```bash
    sudo systemctl restart service_name
    ```
5.  **Enable a service at boot**:

    ```bash
    sudo systemctl enable service_name
    ```
6.  **Disable a service at boot**:

    ```bash
    sudo systemctl disable service_name
    ```

#### **Compression and Archiving**

1.  **Compress files (tar.gz)**:

    ```bash
    tar -czvf archive.tar.gz file1 file2
    ```
2.  **Extract tar.gz files**:

    ```bash
    tar -xzvf archive.tar.gz
    ```
3.  **Zip a file**:

    ```bash
    zip archive.zip file1 file2
    ```
4.  **Unzip a file**:

    ```bash
    unzip archive.zip
    ```

#### **Shell Script Creation & Execution**

1.  **Create and run a shell script with executable permissions**:

    ```bash
    echo '#!/bin/bash\necho "Hello, World!"' > script.sh && chmod +x script.sh && ./script.sh
    ```

#### **Permissions**

1.  **Change permissions of a file**:

    ```bash
    chmod 755 file.txt
    ```
2.  **Change ownership of a file**:

    ```bash
    sudo chown user:user file.txt
    ```
3.  **Change permissions recursively**:

    ```bash
    chmod -R 755 /path/to/directory
    ```

#### **Package Management (Debian-based systems)**

1.  **Update the package list**:

    ```bash
    sudo apt update
    ```
2.  **Upgrade all packages**:

    ```bash
    sudo apt upgrade
    ```
3.  **Install a package**:

    ```bash
    sudo apt install package_name
    ```
4.  **Uninstall a package**:

    ```bash
    sudo apt remove package_name
    ```
5.  **Purge a package (completely remove config files as well)**:

    ```bash
    sudo apt purge package_name
    ```
6.  **Search for a package**:

    ```bash
    apt search package_name
    ```

#### **System Information**

1.  **Check disk usage**:

    ```bash
    df -h
    ```
2.  **Check memory usage**:

    ```bash
    free -h
    ```
3.  **Check CPU usage**:

    ```bash
    top
    ```
4.  **Check system uptime**:

    ```bash
    uptime
    ```

These commands will give you essential control over Linux operations.
