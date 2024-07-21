# About Apache Kafka
- Apache Kafka is a distributed event store and stream-processing platform. Designed as an open-source system by the Apache Software Foundation, it is written in Java and Scala.
- Apache Kafka is like a communication system that helps different parts of a computer system to exchange data by publishing and subscribing to a particular topic.
- In Kafka , there is a sender or a producer which published the data into Kafka and the receiver or consumer can consume the data by subscribing the topic for which they required data in Kafka.

![image](https://github.com/user-attachments/assets/ac855fe5-ebb7-4568-9e6f-4af8cb375f95)

- Imagine you have a social media platform where users post updates, and you want these updates to appear in the feeds of all their friends in real-time. When a user posts an update, the social media platform sends this update to Kafka, which acts like a central hub. Kafka then stores the update in a specific category called a topic, let's say user-updates. Friends of the user have systems that check this user-updates topic in Kafka. As soon as the update is stored, these systems read the new update from Kafka and immediately show it in the friends' activity feeds. This way, all friends see the user's update in real-time. Kafka ensures that the updates are delivered reliably and can handle a large number of updates simultaneously, keeping the social media experience smooth and instant for all users.
- Example
  - LinkedIn: Kafka was originally developed at LinkedIn to handle large-scale data streams efficiently.
  - Twitter : Handling high-volume real-time data, such as tweets, retweets, and likes
  - Netflix : Kafka helps Netflix process and analyze billions of events per day, ensuring a seamless streaming experience.
  - Uber : Kafka helps Uber manage high volumes of real-time data to optimize rides and provide accurate pricing.
- Kafka is a distributed publish-subscribe messaging system. It has a full queue that can accept large amounts of message data. With Kafka, applications can write and read data on topics. A topic presents a category for labeling data. Furthermore, the application can receive messages from one or more categories.
- Apache Kafka can be thought of as a robust and scalable messaging system that allows the seamless transfer of data streams between different applications or systems. It serves as a highly efficient intermediary platform, enabling real-time data processing, analysis, and integration across diverse components.
- **Apache Kafka is an event streaming platform. A streaming platform is a system that allows you to continuously collect, process, and deliver streams of data in real time. Instead of waiting for a batch of data to be processed all at once, data is processed as it arrives.  Actions are taken immediately as data arrives, without waiting for batch processing.It can handle data from many devices and process it simultaneously. Different applications can consume and process the same data in various ways.**
- Technically speaking, event streaming is the practice of capturing data in real-time from event sources like databases, sensors, mobile devices, cloud services, and software applications in the form of streams of events; storing these event streams durably for later retrieval; manipulating, processing, and reacting to the event streams in real-time.
- Example, when a user books a cab using uber, the live location tracking is shown to the user. So if uber does not uses kafka, then on every location a informations needs to be inserted into database. Post insertion, the user who has booked the cab will receive information of location where the vehicle is. Now in case of real time, there can be huge number of customers who books cab and requires live location tracking for their booked vehicle. This unfortunately would crash the database, since there will be much load on it. Multiple read/write operations will be done on it. So in such scenarios we required high throughput applications which can process large amounts of data quickly. Thus, kafka help us to provide high throughput by measuring how many messages a consumer or producer can process in a given time interval, typically in terms of records per second or megabytes per second.

## Why Kafka?

- **High Throughput and Low Latency:** Kafka is designed to handle large volumes of data with minimal delay, making it suitable for real-time applications.
- **Scalability:** Kafka can easily scale horizontally by adding more brokers (servers), allowing it to handle increasing data loads seamlessly.
- **Durability and Reliability:** Kafka persists messages on disk and replicates them across multiple brokers, ensuring data is not lost and can be recovered even in case of failures.
- **Fault Tolerance:** Kafka’s replication mechanism ensures that even if some brokers fail, the system continues to function without data loss. If error occurs we can still get the data without losing it.
- **Distributed Architecture:** Kafka's distributed nature allows it to be deployed across multiple data centers and geographies, supporting a wide range of use cases.
- **Exactly-Once Semantics:** Kafka provides exactly-once processing semantics, which ensures that messages are processed only once, avoiding duplication.
- **Strong Community and Ecosystem:** Kafka has a large and active community, along with a rich ecosystem of tools and connectors that make integration and usage easier.

## Kafka Architecture

![image](https://github.com/user-attachments/assets/8511e366-b88e-413d-80aa-90e0134d4264)

- **Kafka Cluster:** A Kafka cluster is a system that comprises of different brokers, topics, and their respective partitions. Data is written to the topic within the cluster and read by the cluster itself.
- **Producers:** A producer sends or writes data/messages to the topic within the cluster. In order to store a huge amount of data, different producers within an application send data to the Kafka cluster.
- **Consumers:** A consumer is the one that reads or consumes messages from the Kafka cluster. There can be several consumers consuming different types of data form the cluster. The beauty of Kafka is that each consumer knows from where it needs to consume the data.
- **Brokers:** A Kafka server is known as a broker. A broker is a bridge between producers and consumers. If a producer wishes to write data to the cluster, it is sent to the Kafka server. All brokers lie within a Kafka cluster itself. Also, there can be multiple brokers.
- **Topics:** It is a common name or a heading given to represent a similar type of data. In Apache Kafka, there can be multiple topics in a cluster. Each topic specifies different types of messages.
- **Partitions:** The data or message is divided into small subparts, known as partitions. Each partition carries data within it having an offset value. The data is always written in a sequential manner. We can have an infinite number of partitions with infinite offset values. However, it is not guaranteed that to which partition the message will be written. Sub-divisions of topics. Each topic is split into multiple partitions for scalability and parallel processing. It is used to distribute data across multiple servers and allow parallel processing.
- **ZooKeeper:**  A centralized service for maintaining configuration information and coordinating distributed processes. It is used to manage Kafka brokers, track the status of nodes, and ensure high availability. Zookeeper keeps track of which brokers are active and which partitions they are managing. A ZooKeeper is used to store information about the Kafka cluster and details of the consumer clients. It manages brokers by maintaining a list of them. Also, a ZooKeeper is responsible for choosing a leader for the partitions. If any changes like a broker die, new topics, etc., occurs, the ZooKeeper sends notifications to Apache Kafka. A ZooKeeper is designed to operate with an odd number of Kafka servers. Zookeeper has a leader server that handles all the writes, and rest of the servers are the followers who handle all the reads. However, a user does not directly interact with the Zookeeper, but via brokers. No Kafka server can run without a zookeeper server. It is mandatory to run the zookeeper server.

![image](https://github.com/user-attachments/assets/e1995947-07a6-49ad-b800-8912e630e0f0)

