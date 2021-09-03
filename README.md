STEPS TO INSTALL APACHE KAFKA ON WINDOWS

1. got to https://kafka.apache.org/downloads

2. find link for download

3. Unzip and Extract 

4. Rename it to kafka, remove version

5. Place it in your c drive

6. Inside C:\kafka\config, we can see server.properties and zookeeper.properties

Let us change configuration

7. Open server.properties, search for log, alter 

log.dirs=c:/kafka/kafka-logs

8. Open zookeeper.properties,  

now we need to alter working directory for zookeeper

dataDir=c:/kafka/zookeeper-data

so all our dara logs will be going to kafka folder

Let us open command prompt, and open kafka and zookeeper

cmd

9. Go to kafka folder, cd c:/kafka

10. here, we need to start our zookeeper


11. .\bin\windows\zookeeper-server-start.bat 
than we need to give configuraton file, with that configuration file, server will be started

12 .\bin\windows\zookeeper-server-start.bat .\config\zookeeper.properties

you can see zookeeper is started on port number 2181


13. Let us open another command prompt and open apache kafka 

cmd 

cd c:\kafka

14. .\bin\windows\kafka-server-start.bat .\config\server.properties

15. Let us create another terminal and create topic.

16. cd c:\kafka

17. To create a topic 

.\bin\windows\kafka-topics.bat --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1  --topic Testtopic

Testtopic is name of topic, --replication-factor and --partitions are 1, as we are not using cluster-based.

create another topic 

.\bin\windows\kafka-topics.bat --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1  --topic NewTopic

18. To list all topics

.\bin\windows\kafka-topics.bat --list --zookeeper localhost:2181

19. Now, Let us add messages into topic

open new cmd

cd c:\kafka

next, 

.\bin\windows\kafka-console-producer.bat --broker-list localhost:9092 --topic Testtopic 

After hitting enter button, it will open sub console-producer,  where we can enter messages

> Test Input Data
>New Data
>Welcome to JCoder
>Happy Coding!!!


20. Let us consume all messages from Topic

open terminal

cd c:\kafka

.\bin\windows\kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic Testtopic --from-beginning

here we are bootstraping the server and we are consuming messages from beginning

Following is output, we can see all messages that we produced

Test Input Data
New Data
Welcome to JCoder
Happy Coding!!!




where 9092 is default port for kafka 







# Steps-to-create-Kafka-topic-on-Windows
