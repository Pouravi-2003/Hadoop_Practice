# Hadoop_Practice
## some local system (Linux) terminal command
```bash
## check present workdir
abc@aed156c6f206:~/workspace$ pwd
/config/workspace
## creat new dir
abc@aed156c6f206:~/workspace$ mkdir test
## change directory path
abc@aed156c6f206:~/workspace$ cd test
## back in previous directory
abc@aed156c6f206:~/workspace/test$ cd ..
## copy a file into a specific directory
abc@aed156c6f206:~/workspace$ cp tree.csv test
## check files name in present directory
abc@aed156c6f206:~/workspace$ ls
README.md  test  tree.csv
## how to delete a file from a directory
abc@aed156c6f206:~/workspace/test$ rm tree.csv ## It will delete the file from test folder
## check categories and data in csv file
abc@aed156c6f206:~/workspace$ cat tree.csv
## move a file into another directory
abc@aed156c6f206:~/workspace$ mv tree.csv test
## delete specific directory
abc@aed156c6f206:~/workspace$ rmdir test
```
#
## Hadoop Command
- ### Hadoop directory create
```bash
abc@1200cd74ef03:~/workspace$ hadoop fs -mkdir /hadoop-test-1
```
- ### Hadoop check directory 
```bash
abc@1200cd74ef03:~/workspace$ hadoop fs -ls /
Found 1 items
drwxr-xr-x   - abc supergroup          0 2024-05-07 11:50 /hadoop-test-1
```
- ### COPY FROM LOCAL FS TO HDFS
```bash
abc@1200cd74ef03:~/workspace/test$ hadoop fs -copyFromLocal tree.csv /hadoop-test-1
2024-05-07 12:02:06,635 INFO sasl.SaslDataTransferClient: SASL encryption trust check: localHostTrusted = false, remoteHostTrusted = false
abc@1200cd74ef03:~/workspace/test$ hadoop fs -ls /
Found 1 items
drwxr-xr-x   - abc supergroup          0 2024-05-07 12:02 /hadoop-test-1
abc@1200cd74ef03:~/workspace/test$ hadoop fs -ls /hadoop-test-1
Found 1 items
-rw-r--r--   1 abc supergroup        860 2024-05-07 12:02 /hadoop-test-1/tree.csv
```
- ### COPY File FROM HDFS  TO LOCAL FS
```bash
abc@1200cd74ef03:~/workspace/test$ cd ..
abc@1200cd74ef03:~/workspace$ mkdir results
abc@1200cd74ef03:~/workspace$ hadoop fs -copyToLocal /hadoop-test-1/tree.csv results
2024-05-07 12:10:52,286 INFO sasl.SaslDataTransferClient: SASL encryption trust check: localHostTrusted = false, remoteHostTrusted = false
```
- ### COPY File FROM one folder  TO another in HDFS
```bash
abc@f4a4314bae66:~/workspace/results$ hadoop fs -cp /hadoop-test-2/tree.csv /hadoop-test-3
2024-05-07 12:50:41,433 INFO sasl.SaslDataTransferClient: SASL encryption trust check: localHostTrusted = false, remoteHostTrusted = false
2024-05-07 12:50:41,628 INFO sasl.SaslDataTransferClient: SASL encryption trust check: localHostTrusted = false, remoteHostTrusted = false
```
- ### MOVE File FROM one folder  TO another in HDFS
```bash
abc@f4a4314bae66:~/workspace/results$ hadoop fs -mv /hadoop-test-3/tree.csv /hadoop-test-1
```
- ### Delete file from a folder in HDFS
```bash
abc@f4a4314bae66:~/workspace/results$ hadoop fs -rm /hadoop-test-2/tree.csv
Deleted /hadoop-test-2/tree.csv
```