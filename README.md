# Client-Server-Programming

Distributed programming using Sockets:

What is Socket?




Serializationa and De Serialization:
We now know how to have two JVMs communicate with each other we can establish sockets and they can communicate. we saw that we could have calls like getInputStream() and getOutputStream() to perform the communications. but Input and OutputStream really work at the level of sequence of bytes.Individual JVM may have multiple objects what we really want to communucate are objects.this means we need to find some way of converting the objetcs to bytes(thats called serializing the object) andthen when we receive the sequence of bytes we need to recon struct the copy of the object at JVM B and that's called deserialization.

How can we do this?
1. Custom Ser / Der.
2. Use XML(Can be heaby weight in many cases becuase there is a lot of overhead in metadata.
3. Java Ser / DeSer : Class X implements Serializable once you do that you ahe methods that will automatically convert object to bytes 
4. Interface Definition Language(IDL): Tha main advantage is you can communicate your objects, not just between java processes  but between processes written in other languages like c++ and Python. The disadvantage or the little bit of extra overhead for the developer is that you need to write the interface file. fir example for Protocol Buffer  you need to create something  called a .proto file to essentially mirror your class and define the fields that you want to communicate. if you know for sure that you are only communicating between java processes, then java serialization is a very good way to get started.

Remote Method Invocation (RMI):




Unicast:
Boroadcast:
Multicast:



Publish-Subscrive Model:
A higher level pattern for group communication compared to multicast and this is referred as Publish-Subscribe.
a further generalization of the multicast concept. Inthis pattern, publisher processes add messages to designated topics, and subsriber processes receive those messages by registring on the topics that they are intersted in. A key advantage of of this approach is that publishers  need not be aware of which processes are the subscribers, and vice-versa.A nother advanatage is that it lends otself to very efficeint implementation beacuse it can enable a numnber of communication optimizations, which include batching and topic partitioning across broker nodes. Yet another advantage is improved reliability, beacause broker nodes can replicate messages in a topic, so that if one node hosting a topic fails, the entire publicsh subscribe system cam continue execution with another node that contains a copy of all messages in that topic.

To become a publisher, a process simply needs to create a KafkaProducer object. and use it to perform send() operations to designated topics. Likewise to become a consumer, a process needs to create a KafkaConsumer object, whicj can then  be used to subscribe to topics of interest. The consumer then performs  repeated poll() operations, each of which returns a batch of messages from the requested topics. Kafka 













