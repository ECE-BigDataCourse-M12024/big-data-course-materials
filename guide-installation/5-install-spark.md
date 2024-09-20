# Installation Guide: Apache Spark 3.4.1

## Prerequisites
- Java 8 or later installed
- Python 3.7 or later (for PySpark)
- Hadoop (optional, but recommended)


## Installation Steps

### For Windows:

1. Download Spark:
   - Go to https://downloads.apache.org/spark/spark-3.5.2/spark-3.5.2-bin-hadoop3.tgz

2. Extract the archive:
   - Move the Zip archive to C:\
   - Use 7-Zip or a similar tool to extract the .tgz file and rename to spark-3.5.2
   - Sometimes when extracting you'll have another intermediary folder named 'spark-3.5.2-bin-hadoop3' make sure to have no intermediary folder

3. Set up environment variables:
   - Open "Edit the system environment variables"
   - Add new system variable SPARK_HOME: C:\spark-3.5.2
   - Edit PATH variable, add %SPARK_HOME%\bin

4. Add Hadoop winutils libraries:
   - Copy paste the following files from your Hadoop bin folder at: C:\hadoop-3.3.6\bin\
    *hadoop.dll*
    *hadoop.exp*
    *hadoop.lib*
    *hadoop.pdb*
    *hdfs*
    *hdfs* executable
    *libwinutils.lib*
    *winutils.exe*
    *winutils.pdb*

   - and place them in C:\spark-3.5.2\bin


### For macOS and Linux:

1. Download Spark:
   ```
   wget https://downloads.apache.org/spark/spark-3.5.2/spark-3.5.2-bin-hadoop3.tgz
   ```

2. Extract the archive:
   ```
   tar -xvzf spark-3.4.1-bin-hadoop3.tgz
   ```

3. Move Spark folder:
   ```
   sudo mv spark-3.4.1-bin-hadoop3 /usr/local/spark
   ```

4. Set up environment variables:
   - Edit ~/.bashrc or ~/.zshrc:
     ```
     export SPARK_HOME=/usr/local/spark
     export PATH=$PATH:$SPARK_HOME/bin
     ```
   - Apply changes:
     ```
     source ~/.bashrc  # or ~/.zshrc
     ```

## Verifying Installation

1. Open a new terminal or command prompt
2. Run:
   ```
   spark-shell
   ```
3. You should see the Spark shell interface. Type :quit to exit.

## Install also PySpark

1. Ensure Python is installed and go to VSCode
2. Run:
   ```
   pip install pyspark
   ```

## Troubleshooting

- If you encounter Java-related errors, ensure JAVA_HOME is set correctly
- For "command not found" errors, check if Spark's bin directory is in your PATH
- On Windows, if you see "hadoop.dll" errors, ensure winutils.exe is in the correct location