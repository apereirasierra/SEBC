sudo su
su saturn

hdfs dfs -chown saturn /user/saturn 
hdfs dfs -chown haley /user/haley

hdfs dfs -ls /user
[saturn@ip-172-31-17-111 ec2-user]$ hdfs dfs -ls /user
Found 9 items
drwxr-xr-x   - admin  admin               0 2017-07-21 13:18 /user/admin
drwxr-xr-x   - haley  supergroup          0 2017-07-21 13:09 /user/haley
drwxr-xr-x   - hdfs   supergroup          0 2017-07-21 13:16 /user/hdfs
drwxrwxrwx   - mapred hadoop              0 2017-07-21 11:15 /user/history
drwxrwxr-t   - hive   hive                0 2017-07-21 11:16 /user/hive
drwxrwxr-x   - hue    hue                 0 2017-07-21 11:16 /user/hue
drwxrwxr-x   - oozie  oozie               0 2017-07-21 11:16 /user/oozie
drwxr-xr-x   - saturn supergroup          0 2017-07-21 13:08 /user/saturn
drwxr-x--x   - spark  spark               0 2017-07-21 11:15 /user/spark

As user saturn, use teragen to generate a 65,536,000-record dataset
time sudo -u hdfs hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar teragen -Dmapred.map.tasks=12 -Ddfs.blocksize=33554432 51200000 /user/saturn/tgen5
17/07/21 13:43:41 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-17-111.us-west-2.compute.internal/172.31.17.111:8032
17/07/21 13:43:42 INFO terasort.TeraGen: Generating 51200000 using 12
17/07/21 13:43:42 INFO mapreduce.JobSubmitter: number of splits:12
17/07/21 13:43:42 INFO Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
17/07/21 13:43:42 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1500650106787_0001
17/07/21 13:43:42 INFO impl.YarnClientImpl: Submitted application application_1500650106787_0001
17/07/21 13:43:42 INFO mapreduce.Job: The url to track the job: http://ip-172-31-17-111.us-west-2.compute.internal:8088/proxy/application_1500650106787_0001/
17/07/21 13:43:42 INFO mapreduce.Job: Running job: job_1500650106787_0001
17/07/21 13:43:50 INFO mapreduce.Job: Job job_1500650106787_0001 running in uber mode : false
17/07/21 13:43:50 INFO mapreduce.Job:  map 0% reduce 0%
17/07/21 13:44:07 INFO mapreduce.Job:  map 9% reduce 0%
17/07/21 13:44:09 INFO mapreduce.Job:  map 28% reduce 0%
17/07/21 13:44:10 INFO mapreduce.Job:  map 40% reduce 0%
17/07/21 13:44:12 INFO mapreduce.Job:  map 41% reduce 0%
17/07/21 13:44:13 INFO mapreduce.Job:  map 43% reduce 0%
17/07/21 13:44:15 INFO mapreduce.Job:  map 55% reduce 0%
17/07/21 13:44:16 INFO mapreduce.Job:  map 56% reduce 0%
17/07/21 13:44:18 INFO mapreduce.Job:  map 58% reduce 0%
17/07/21 13:44:21 INFO mapreduce.Job:  map 65% reduce 0%
17/07/21 13:44:22 INFO mapreduce.Job:  map 66% reduce 0%
17/07/21 13:44:22 INFO mapreduce.Job:  map 66% reduce 0%
17/07/21 13:44:24 INFO mapreduce.Job:  map 67% reduce 0%
17/07/21 13:44:27 INFO mapreduce.Job:  map 76% reduce 0%
17/07/21 13:44:29 INFO mapreduce.Job:  map 77% reduce 0%
17/07/21 13:44:33 INFO mapreduce.Job:  map 84% reduce 0%
17/07/21 13:44:39 INFO mapreduce.Job:  map 92% reduce 0%
17/07/21 13:44:44 INFO mapreduce.Job:  map 98% reduce 0%
17/07/21 13:44:45 INFO mapreduce.Job:  map 100% reduce 0%
17/07/21 13:44:45 INFO mapreduce.Job: Job job_1500650106787_0001 completed successfully
17/07/21 13:44:45 INFO mapreduce.Job: Counters: 33
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=1531598
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=1025
		HDFS: Number of bytes written=5120000000
		HDFS: Number of read operations=48
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=24
	Job Counters 
		Launched map tasks=12
		Other local map tasks=12
		Total time spent by all maps in occupied slots (ms)=605672
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=605672
		Total vcore-milliseconds taken by all map tasks=605672
		Total megabyte-milliseconds taken by all map tasks=620208128
	Map-Reduce Framework
		Map input records=51200000
		Map output records=51200000
		Input split bytes=1025
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=1998
		CPU time spent (ms)=116390
		Physical memory (bytes) snapshot=4316897280
		Virtual memory (bytes) snapshot=19279785984
		Total committed heap usage (bytes)=6627000320
		Peak Map Physical memory (bytes)=381095936
		Peak Map Virtual memory (bytes)=1615835136
	org.apache.hadoop.examples.terasort.TeraGen$Counters
		CHECKSUM=109963291816450258
	File Input Format Counters 
		Bytes Read=0
	File Output Format Counters 
		Bytes Written=5120000000

real	1m6.612s
user	0m4.997s
sys	0m0.255s

The command and output of hdfs dfs -ls /user/saturn/tgen
sudo hdfs dfs -ls /user/saturn/tgen5
Found 13 items
-rw-r--r--   3 hdfs supergroup          0 2017-07-21 13:44 /user/saturn/tgen5/_SUCCESS
-rw-r--r--   3 hdfs supergroup  426666700 2017-07-21 13:44 /user/saturn/tgen5/part-m-00000
-rw-r--r--   3 hdfs supergroup  426666700 2017-07-21 13:44 /user/saturn/tgen5/part-m-00001
-rw-r--r--   3 hdfs supergroup  426666600 2017-07-21 13:44 /user/saturn/tgen5/part-m-00002
-rw-r--r--   3 hdfs supergroup  426666700 2017-07-21 13:44 /user/saturn/tgen5/part-m-00003
-rw-r--r--   3 hdfs supergroup  426666700 2017-07-21 13:44 /user/saturn/tgen5/part-m-00004
-rw-r--r--   3 hdfs supergroup  426666600 2017-07-21 13:44 /user/saturn/tgen5/part-m-00005
-rw-r--r--   3 hdfs supergroup  426666700 2017-07-21 13:44 /user/saturn/tgen5/part-m-00006
-rw-r--r--   3 hdfs supergroup  426666700 2017-07-21 13:44 /user/saturn/tgen5/part-m-00007
-rw-r--r--   3 hdfs supergroup  426666600 2017-07-21 13:44 /user/saturn/tgen5/part-m-00008
-rw-r--r--   3 hdfs supergroup  426666700 2017-07-21 13:44 /user/saturn/tgen5/part-m-00009
-rw-r--r--   3 hdfs supergroup  426666700 2017-07-21 13:44 /user/saturn/tgen5/part-m-00010
-rw-r--r--   3 hdfs supergroup  426666600 2017-07-21 13:44 /user/saturn/tgen5/part-m-00011

The command and output of hadoop fsck -blocks /user/saturn
hdfs fsck -blocks /user/saturn
Connecting to namenode via http://ip-172-31-17-111.us-west-2.compute.internal:50070
FSCK started by root (auth:SIMPLE) from /172.31.17.111 for path /user/saturn at Fri Jul 21 13:46:35 EDT 2017
.............Status: HEALTHY
 Total size:	5120000000 B
 Total dirs:	2
 Total files:	13
 Total symlinks:		0
 Total blocks (validated):	156 (avg. block size 32820512 B)
 Minimally replicated blocks:	156 (100.0 %)
 Over-replicated blocks:	0 (0.0 %)
 Under-replicated blocks:	0 (0.0 %)
 Mis-replicated blocks:		0 (0.0 %)
 Default replication factor:	3
 Average block replication:	3.0
 Corrupt blocks:		0
 Missing replicas:		0 (0.0 %)
 Number of data-nodes:		3
 Number of racks:		1
FSCK ended at Fri Jul 21 13:46:35 EDT 2017 in 9 milliseconds


The filesystem under path '/user/saturn' is HEALTHY


