# Installation Guide: Maven
Apache Maven est un outil de gestion et d'automatisation de production des projets logiciels Java

1. **Install Maven** 
    - Go to : https://maven.apache.org/download.cgi
    - Download the Binary zip archive (e.g., apache-maven-3.8.8-bin.zip)
    - Create a folder (e.g., C:\Apache\maven)
    - Extract the downloaded zip file into this folder

2. **Set up Envrt variables**
   - Right-click on 'This PC' or 'My Computer' and select 'Properties'
   - Click on 'Advanced system settings'
   - Click on 'Environment Variables'
   - Under 'System variables', click 'New'
   - Set Variable name as 'MAVEN_HOME'
   - Set Variable value as the path to your Maven folder (e.g., C:\Program Files\Apache\maven)
   - Click 'OK'
   - Find 'Path' under 'System variables', select it and click 'Edit'
   - Click 'New' and add '%MAVEN_HOME%\bin'
   - Click 'OK' to close all dialogs
   - Restart any open command prompts for the changes to take effect

3. **Verify**
Open a terminal and type the following command:
```
mvn -version
```

4. **Set up in VSCode**
- Open VS Code settings (File > Preferences > Settings or Ctrl+,).
- Search for "maven" in the settings search bar.
- Look for "Maven: Executable Path" and set it to the path of your Maven installation if it's not automatically detected ie: C:\apache-maven-3.8.8\bin\mvn.cmd