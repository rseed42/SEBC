## Snapshot

Clone repo to edge node

git clone https://https://github.com/rseed42/SEBC/

Create the archive

tar -czf SEBC.tar.gz SEBC

Upload to HDFS

hdfs dfs -mkdir /user/rseed42/precious
hdfs dfs -put SEBC.tar.gz /user/rseed42/

Make directory snapshottable (as hdfs admin)

su hdfs
hdfs dfsadmin -allowSnapshot /user/rseed42/precious

Create snapshot

hdfs dfs -createSnapshot /user/rseed42/precious sebc-hdfs-test

Try delete /user/rseed42/precious

[rseed42@ip-172-31-23-134 script]$ hdfs dfs -rm -r -skipTrash /user/rseed42/precious
rm: The directory /user/rseed42/precious cannot be deleted since /user/rseed42/precious is snapshottable and already has snapshots

Delete zip file

hdfs dfs -rm -skipTrash /user/rseed42/precious/SEBC.tar.gz

Check snapshots

[rseed42@ip-172-31-23-134 script]$ hdfs dfs -ls /user/rseed42/precious/.snapshot
Found 1 items
drwxr-xr-x   - rseed42 rseed42          0 2016-11-16 09:16 /user/rseed42/precious/.snapshot/sebc-hdfs-test

Restore our precious file from the saved snapshot

hdfs dfs -cp /user/rseed42/precious/.snapshot/sebc-hdfs-test/SEBC.tar.gz /user/rseed42/precious
