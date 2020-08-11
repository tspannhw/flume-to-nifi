## flume-to-nifi

Examples for Apache Flume to Apache NiFi

Remember Flume?   Me neither.   Let's try to do these things in Apache NiFi.


### Paul Vidal Asked for a Read me

## Articles

* https://dev.to/tspannhw/migrating-apache-flume-flows-to-apache-nifi-jms-to-x-and-x-to-jms-1g02
* https://www.datainmotion.dev/2019/10/migrating-apache-flume-flows-to-apache_15.html
* https://www.datainmotion.dev/2019/10/migrating-apache-flume-flows-to-apache_42.html

## Use Cases - NiFi Flows

* Logs to HDFS:   Flume_Log_to_HDFS.xml
* Kafka: Kafka_Example.xml
* JDBC/RDBMS/Database: RDBMSFlume.xml
* Twitter to Kafka: TwitterToKafka.xml
* Kafka to Parquet: kafkatoparquet.xml.   (could be HDFS, Files, S3, ADLS)
* PutParquet: putparquet.xml


## Flows

![Example NiFi Flow](https://raw.githubusercontent.com/tspannhw/flume-to-nifi/master/HTTPtoKafka.png)

![Kafka](https://raw.githubusercontent.com/tspannhw/flume-to-nifi/master/KafkaToParquet.png)


## Log Files to HDFS

### NiFi File Filter / Reg Ex To Match Input Name Patterns: (wifi).*log

#### UpdateAttribute: Set File Name: ${filename:replaceAll(':', ''):replaceAll('|','')}

Also remove invalid characters from HDFS filename output

https://hadoop.apache.org/docs/r2.5.2/hadoop-project-dist/hadoop-common/filesystem/model.html 

NiFi Output: Attribute Values absolute.path /var/log/ file.creationTime 2019-08-12T10:08:53-0400 file.group wheel file.lastAccessTime 2019-08-12T10:08:53-0400 file.lastModifiedTime 2019-08-12T10:08:53-0400 file.owner root file.permissions rw-r--r-- file.size 271413 filename wifi-08-12-2019__10:08:53.107.log path ./ uuid 6693546e-1241-4625-bbd8-b9dd5da9281a

hdfs dfs -ls /flume Found 7 items -rw-r--r-- 1 tspann hdfs 120824 2019-08-13 19:49 /flume/wifi-08-12-2019__100647.406.log -rw-r--r-- 1 tspann hdfs 125888 2019-08-13 19:49 /flume/wifi-08-12-2019__100651.863.log -rw-r--r-- 1 tspann hdfs 252917 2019-08-13 19:49 /flume/wifi-08-12-2019__100839.901.log -rw-r--r-- 1 tspann hdfs 255873 2019-08-13 19:49 /flume/wifi-08-12-2019__100845.958.log -rw-r--r-- 1 tspann hdfs 271315 2019-08-13 19:49 /flume/wifi-08-12-2019__100848.189.log -rw-r--r-- 1 tspann hdfs 271413 2019-08-13 19:49 /flume/wifi-08-12-2019__100853.107.log -rw-r--r-- 1 tspann hdfs 17078 2019-08-13 19:49 /flume/wifi.log

