# Installation Guide: Hadoop 3.3.6 for Windows

Hadoop is a framework that allows for the distributed processing of large data sets across clusters of computers.


# Windows
## Installation Steps

1. **Download Hadoop**
   - Go to: https://downloads.apache.org/hadoop/common/hadoop-3.3.6/
   - Download the "hadoop-3.3.6.tar.gz" archive

2. **Extract the Archive**
   - Open a terminal and navigate to your Downloads folder
   - Run the following command:
     ```
     tar -xvzf hadoop-3.3.6.tar.gz
     ```

3. **Move Hadoop Folder**
   - Move the unzipped `hadoop-3.3.6` folder from Downloads to `C:\`

4. **Install Hadoop Native IO Binary**
   - Open a PowerShell terminal as administrator
   - Make sure you're located at `C:\`
   - Run the following commands:
     ```powershell
     $dest_dir = "C:"
     $client = New-Object System.Net.WebClient
     $client.DownloadFile("https://github.com/cdarlint/winutils/raw/master/hadoop-3.3.6/bin/hadoop.dll",$dest_dir+"\hadoop-3.3.6\bin\"+"hadoop.dll")
     $client.DownloadFile("https://github.com/cdarlint/winutils/raw/master/hadoop-3.3.6/bin/hadoop.exp",$dest_dir+"\hadoop-3.3.6\bin\"+"hadoop.exp")
     $client.DownloadFile("https://github.com/cdarlint/winutils/raw/master/hadoop-3.3.6/bin/hadoop.lib",$dest_dir+"\hadoop-3.3.6\bin\"+"hadoop.lib")
     $client.DownloadFile("https://github.com/cdarlint/winutils/raw/master/hadoop-3.3.6/bin/hadoop.pdb",$dest_dir+"\hadoop-3.3.6\bin\"+"hadoop.pdb")
     $client.DownloadFile("https://github.com/cdarlint/winutils/raw/master/hadoop-3.3.6/bin/libwinutils.lib",$dest_dir+"\hadoop-3.3.6\bin\"+"libwinutils.lib")
     $client.DownloadFile("https://github.com/cdarlint/winutils/raw/master/hadoop-3.3.6/bin/winutils.exe",$dest_dir+"\hadoop-3.3.6\bin\"+"winutils.exe")
     $client.DownloadFile("https://github.com/cdarlint/winutils/raw/master/hadoop-3.3.6/bin/winutils.pdb",$dest_dir+"\hadoop-3.3.6\bin\"+"winutils.pdb")
     ```

5. **Configure Environment Variables**
   - Open the Windows search bar and search for 'Edit the system environment variables'
   - Click on 'Environment Variables'
   - Under 'System variables', click 'New'
   - Set Variable name as `HADOOP_HOME` and Variable value as `C:\hadoop-3.3.6`
   - Find the 'Path' variable under 'System variables' and click 'Edit'
   - Click 'New' and add `%HADOOP_HOME%\bin`
   - Click 'OK' to close all dialogs


## Verifying Installation
1. Open a new Command Prompt
2. Run the following command:
   ```
   hadoop version
   ```

3. If the installation is successful, you should see output similar to:
   ```
   Hadoop 3.3.6
   Source code repository https://github.com/apache/hadoop.git -r 1be78238728da9266a4f88195058f08fd012bf9c
   Compiled by ubuntu on 2023-06-18T08:22Z
   Compiled with protoc 3.7.1
   From source with checksum 5652179ad55f76cb287d9c633bb53bbd
   This command was run using /usr/local/hadoop/share/hadoop/common/hadoop-common-3.3.6.jar
   ```

## Troubleshooting
- If you encounter an error related to JAVA_HOME, ensure that you've correctly set the JAVA_HOME environment variable. If you still encounter the issue, modify directly the Hadoop Configuration file :
   - Open `C:\hadoop-3.3.6\etc\hadoop\hadoop-env.cmd` in a text editor
   - Find the line that sets JAVA_HOME and replace it with:
     ```
     set JAVA_HOME=C:\Java\jdk-1.8
     ```
   - Find the line that sets HADOOP_OPTS and update it to:
     ```
     set HADOOP_OPTS="-Xmx512m %HADOOP_OPTS%"
     ```
- If you're still experiencing issues, double-check that all environment variables are set correctly and that the Hadoop binaries are in your system PATH.
- Make sure you've restarted your command prompt after making changes to environment variables.


# Linux and MacOS

1. **Download Hadoop**
   - Open a terminal and run:
     ```
     wget https://downloads.apache.org/hadoop/common/hadoop-3.3.6/hadoop-3.3.6.tar.gz
     ```
   - If `wget` is not available, you can use `curl`:
     ```
     curl -O https://downloads.apache.org/hadoop/common/hadoop-3.3.6/hadoop-3.3.6.tar.gz
     ```

2. **Extract the Archive**
   ```
   tar -xvzf hadoop-3.3.6.tar.gz
   ```

3. **Move Hadoop Folder**
   ```
   sudo mv hadoop-3.3.6 /usr/local/hadoop
   ```

4. **Set Environment Variables**
   - Open your shell configuration file (`~/.bashrc` for Bash, `~/.zshrc` for Zsh) in a text editor:
     ```
     nano ~/.bashrc  # or ~/.zshrc
     ```
   - Add the following lines at the end of the file:
     ```
     export HADOOP_HOME=/usr/local/hadoop
     export HADOOP_INSTALL=$HADOOP_HOME
     export HADOOP_MAPRED_HOME=$HADOOP_HOME
     export HADOOP_COMMON_HOME=$HADOOP_HOME
     export HADOOP_HDFS_HOME=$HADOOP_HOME
     export YARN_HOME=$HADOOP_HOME
     export HADOOP_COMMON_LIB_NATIVE_DIR=$HADOOP_HOME/lib/native
     export PATH=$PATH:$HADOOP_HOME/sbin:$HADOOP_HOME/bin
     export HADOOP_OPTS="-Djava.library.path=$HADOOP_HOME/lib/native"
     ```
   - Save and close the file
   - Apply the changes:
     ```
     source ~/.bashrc  # or ~/.zshrc
     ```

5. **Configure Hadoop**
   - Edit `$HADOOP_HOME/etc/hadoop/hadoop-env.sh`:
     ```
     nano $HADOOP_HOME/etc/hadoop/hadoop-env.sh
     ```
   - Set JAVA_HOME by adding or uncommenting this line:
     ```
     export JAVA_HOME=/path/to/your/java/home
     ```
   - Save and close the file

6. **Set Up SSH**
   - Generate an SSH key if you haven't already:
     ```
     ssh-keygen -t rsa -P ""
     ```
   - Add the key to authorized_keys:
     ```
     cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
     ```
   - Ensure you can SSH to localhost without a password:
     ```
     ssh localhost
     ```

## Verifying Installation
1. Open a new terminal window
2. Run the following command:
   ```
   hadoop version
   ```

3. If the installation is successful, you should see output similar to:
   ```
   Hadoop 3.3.6
   Source code repository https://github.com/apache/hadoop.git -r 1be78238728da9266a4f88195058f08fd012bf9c
   Compiled by ubuntu on 2023-06-18T08:22Z
   Compiled with protoc 3.7.1
   From source with checksum 5652179ad55f76cb287d9c633bb53bbd
   This command was run using /usr/local/hadoop/share/hadoop/common/hadoop-common-3.3.6.jar
   ```

## Troubleshooting
- If you encounter "Permission denied" errors, ensure that the user has write permissions in the Hadoop directories.
- For "connection refused" errors, check if SSH is properly configured and the Hadoop processes are running.
- If you see Java-related errors, double-check your JAVA_HOME setting in hadoop-env.sh and your system's environment variables.
