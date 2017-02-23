# assignment-4.6
QN-2 Imagine that you are uploading a file of 500MB into HDFS.100MB of data is successfully
uploaded into HDFS and another client wants to read the uploaded data while the upload is still in
progress. What will happen in such a scenario, will the 100 MB of data that is uploaded will it be
displayed?
1.We assume that we are using a Hadoop 2.x and we have configured the block size to be 100 MB and replication factor of 3
2.So we have 5 blocks 1,2,3,4,5.
2.First client will ask Namenode and namenode after checking permission give the datanode where first bock(100Mb) is written and Datanode simultaneously makes replicas of blocks after getting permission from namenode.
3. Once the block is copied and replicated to the datanodes, client will get the confirmation about the Block 1 storage and then, it will initiate the same process for next block “Block 2”.Now block 2 will be write on DataNode as per  permission given by namenode
4.So, during this process if 1st block of 100 MB is written to HDFS and the next block has been started by the client to store then 1st block will be visible to readers. Only the current block being written will not be visible by the readers.
