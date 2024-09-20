# Installation Guide: Oracle JDK 8

Java Development Kit (JDK) is essential for developing (Development tools) and running (JRE) Java applications and is often required for various Big Data tools (like Hadoop). 


## Important Note

Oracle now requires an account to download JDK 8. If you don't have an Oracle account, you'll need to create one before downloading. Alternatively, you might consider using OpenJDK, which is an open-source alternative to Oracle's JDK.

## Installation Steps

### For Windows:

1. Go to the Oracle JDK 8 download page: https://www.oracle.com/java/technologies/javase/javase8u211-later-archive-downloads.html
2. Accept the license agreement and download the Windows x64 installer.
3. Once downloaded, run the installer (e.g., `jdk-8u301-windows-x64.exe`).
4. Follow the installation wizard, using the default options **except for the path of installation** of the resource. Choose 'C:\'.
5. After installation, set the JAVA_HOME environment variable:
   - Right-click on 'This PC' or 'My Computer' and select 'Properties'.
   - Click on 'Advanced system settings'.
   - Click on 'Environment Variables'.
   - Under 'System variables', click 'New'.
   - Set Variable name as `JAVA_HOME` and Variable value as the JDK installation path (e.g., `C:\Java\jdk1.8.0_301`).
6. Add Java to the PATH:
   - Edit the 'Path' variable under 'System variables'.
   - Add `%JAVA_HOME%\bin` to the list.
7. Verify the installation by opening Command Prompt and typing:
   ```
   java -version
   javac -version
   ```

### For macOS:

1. Go to the Oracle JDK 8 download page: https://www.oracle.com/java/technologies/javase/javase8u211-later-archive-downloads.html
2. Accept the license agreement and download the macOS x64 DMG installer.
3. Once downloaded, open the DMG file and run the installer package.
4. Follow the installation wizard, using the default options unless you have specific preferences.
5. The installer should set up the necessary environment variables automatically.
6. Verify the installation by opening Terminal and typing:
   ```
   java -version
   javac -version
   ```

### For Linux (Ubuntu/Debian):

1. Go to the Oracle JDK 8 download page: https://www.oracle.com/java/technologies/javase/javase8u211-later-archive-downloads.html
2. Accept the license agreement and download the Linux x64 tar.gz archive.
3. Open Terminal and navigate to the directory where you downloaded the archive.
4. Extract the archive:
   ```
   tar -xvf jdk-8u301-linux-x64.tar.gz
   ```
5. Move the extracted folder to /usr/lib:
   ```
   sudo mv jdk1.8.0_301 /usr/lib/jvm/
   ```
6. Set up environment variables by editing ~/.bashrc:
   ```
   nano ~/.bashrc
   ```
   Add these lines at the end of the file:
   ```
   export JAVA_HOME=/usr/lib/jvm/jdk1.8.0_301
   export PATH=$PATH:$JAVA_HOME/bin
   ```
7. Save the file and run:
   ```
   source ~/.bashrc
   ```
8. Update alternatives:
   ```
   sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jdk1.8.0_301/bin/java" 1
   sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/lib/jvm/jdk1.8.0_301/bin/javac" 1
   sudo update-alternatives --set java /usr/lib/jvm/jdk1.8.0_301/bin/java
   sudo update-alternatives --set javac /usr/lib/jvm/jdk1.8.0_301/bin/javac
   ```
9. Verify the installation:
   ```
   java -version
   javac -version
   ```

## Verifying Installation

After installation, open a new terminal or command prompt and run:

```
java -version
```

You should see output similar to:

```
java version "1.8.0_301"
Java(TM) SE Runtime Environment (build 1.8.0_301-b09)
Java HotSpot(TM) 64-Bit Server VM (build 25.301-b09, mixed mode)
```

## Troubleshooting

1. If `java -version` doesn't work, ensure that the JAVA_HOME environment variable is set correctly and that Java is in your PATH.
2. On Windows, you might need to restart your computer after setting environment variables.
3. On Linux, if you're using a different shell than bash, you'll need to modify the appropriate configuration file (e.g., ~/.zshrc for Zsh).