# Run Kafka on Windows Terminal

- Download the file from [kafka official website](https://kafka.apache.org/downloads).
- Extract that file to C drive
- Kafka relies on zookeeper for managing distributed brokers and handling other critical tasks. So first we need to start zookeeper server then we need to start kafka broker server.
- Command to start zookeeper server. **Run the exact command including path** 

```windows
.\bin\windows\zookeeper-server-start.bat .\config\zookeeper.properties
```
![image](https://github.com/user-attachments/assets/8a917e4d-ae03-4993-aca5-b466aafc2349)


- Command to start kafka broker server. **Run the exact command including path** (open this in a new windows terminal)
  
```windows
.\bin\windows\kafka-server-start.bat .\config\server.properties
```

![image](https://github.com/user-attachments/assets/542f676d-220c-4833-a117-f63ec89a6733)


- Default 9092 is the port consume by Kafka server. If required we can change it in the config.properties file.
- Quick guide to start with kafka [commands](https://kafka.apache.org/quickstart)

1. Create a new topic in windows

```windows
bin\windows\kafka-topics.bat --create --topic quickstart-events --bootstrap-server localhost:9092
```

- `--create`: This option specifies that you want to create a new topic. `--topic quickstart-events` : This option specifies the name of the topic you want to create, which in this case is test-topic. `--bootstrap-server localhost:9092`: This specifies the Kafka broker’s address. The --bootstrap-server option provides the initial list of Kafka brokers that your command-line tool should connect to in order to interact with the Kafka cluster.

![image](https://github.com/user-attachments/assets/538ef68a-4b83-4458-b7a1-29f1a70817a4)

- Help

![image](https://github.com/user-attachments/assets/45fd4bd8-8e72-49f6-86f2-9e8c0b9dc85d)

- List topics

![image](https://github.com/user-attachments/assets/5a7ad6ba-f7f4-4f5b-ab0d-f50f3eec1404)

- Produce content inside the topics

```windows
bin\windows\kafka-console-producer.bat --topic quickstart-events --bootstrap-server localhost:9092
```

![image](https://github.com/user-attachments/assets/d171e516-bdb5-4955-82b4-bc640fd80d8d)

- Consumer , consume data from beginning

```windows
bin\windows\kafka-console-consumer.bat --topic quickstart-events --from-beginning --bootstrap-server localhost:9092
```

![image](https://github.com/user-attachments/assets/eab4f8ed-1514-490b-83dd-a0eea74f9028)



https://github.com/user-attachments/assets/b337e5e2-6b22-4859-b1ac-70eb82e4b13f



