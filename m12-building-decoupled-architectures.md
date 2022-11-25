# overview
This module includes the following sections:
1.  Architectural need
2.  Decoupling your architecture
3.  Decoupling with Amazon Simple Queue Service (Amazon SQS)
4.  Decoupling with Amazon Simple Notification Service (Amazon SNS)
5.  Sending messages between cloud applications and on-premises with Amazon MQ

# module objectives
At the end of this module, you should be able to:
-   Differentiate between tightly and loosely coupled architectures
-   Identify how Amazon SQS works and when to use it
-   Identify how Amazon SNS works and when to use it
-   Describe Amazon MQ

# 1.  Architectural need

![](m12-cafe-require.png)
The café’s architecture now supports hundreds of thousands of users. However, the café’s systems are too tightly coupled. It’s difficult to make changes to one layer of the application without affecting the other layers. For example, daily ordering reports are generated from the same web server that also serves the café’s website to customers.

In addition, Frank mentioned that he’s not getting the regular 17:00 report on Fridays. After some investigation, Sofía and Nikhil observe that the scheduled maintenance window coincides with the time that the reporting system attempts to generate the report.

They speak with Olivia, who recommends that they decouple the architecture. By moving the reporting process to another system, the reporting data will not be lost, even if the web server becomes temporarily unavailable. Also, the need to generate a report will be queued and handled.


# 2.  Decoupling your architecture
key takeaways:
-   Tightly coupled systems have chains of tightly integrated components and impede scaling
-   You can implement loose coupling in your system by using managed solutions (such as Elastic Load Balancing) as intermediaries between layers

![](tightly-coupled-architecture-01.png)

![](tightly-coupled-architecture-02.png)

![](forms-system-coupling.png)

![](loosely-coupled-archiecture.png)

![](loosely-coupled-consideration.png)



# 3.  Decoupling with Amazon Simple Queue Service (Amazon SQS)
key takeaways:
-   Amazon SQS is a fully managed, message-queuing service that enables you to decouple application components so they run independently.
-   Amazon SQS supports standard and FIFO queues.
-   A producer sends a message to a queue. A consumer processes and deletes the message during the visibility timeout.
-   Messages that cannot be processed can be sent to a dead letter queue.
-   Long polling is a way to retrieve a large number of messages from your SQS queues.

![](message-queue-decoupling-architecture.png)

![](sqs-01.png)

![](loose-coupling-sqs.png)

![](sqs-uc-01.png)

![](queue-types.png)


![](sqs-feature-01.png)


![](sqs-feature-02.png)

![](sqs-feature-03.png)

![](sqs-message-lifecycle-create.png)

![](sqs-message-lifecycle-create.png)

![](sqs-message-lifecycle-process.png)


![](sqs-message-lifecycle-del.png)

![](decoupling-ex-using-sqs-01.png)

![](message-queue-uc-01.png)

![](message-queue-uc-02.png)




#  4.  Decoupling with Amazon Simple Notification Service (Amazon SNS)
key takeaways:
-   Amazon SNS is a web service that you can use to set up, operate, and send notifications from the cloud
-   Amazon SNS follows the pub/sub messaging paradigm
-   When you use Amazon SNS, you create a topic and set policies that restrict who can publish or subscribe to the topic
-   You can use topics to decouple message publishers from subscribers, fan-out messages to multiple recipients at one time, and eliminate polling in your applications
-   AWS services can publish messages to your SNS topics to trigger event-driven computing and workflows

![](pub-sub-messaging.png)

![](sns.png)

![](support-transport-protocols.png)

![](sns-uc-01.png)


![](sns-consider.png)

![](decoupling-ex-s3-sns.png)

![](sns-vs-sqs.png)


# 5.  Sending messages between cloud applications and on-premises with Amazon MQ
key takeaways:
-   Amazon MQ is a managed message broker service for Apache ActiveMQ that enables you set up and operate message brokers in the cloud
-   Amazon MQ manages the provisioning, setup, and maintenance of ActiveMQ, which is a popular open-source message broker
-   Amazon MQ is compatible with open standard APIs and protocols (that is, JMS, NMS, AMQP, STOMP, MQTT, and WebSockets)
-   You can use Amazon MQ to integrate on-premises and cloud environments by using the network of brokers feature of ActiveMQ

![](amazon-mq-01.png)

![](amazon-mq-02.png)


![](mq-vs-sqs-sns.png)


# quiz
Look at the answer choices and rule them out based on the keywords.

![](m12-quiz.png)

# links
If you want to learn more about the topics covered in this module, you might find the following additional resources helpful:

-   Building Loosely Coupled, Scalable, C# Applications with Amazon SQS and Amazon SNS
    
-   Amazon SQS resources
    
-   Amazon SNS resources
    
-   Amazon MQ resources