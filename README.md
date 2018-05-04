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
a further generalization of the multicast concept.
In this pattern, publisher processes add messages to designated topics, and subsriber processes receive those messages by registring on the topics that they are intersted in i.e. Producers are adding messgaes to a topic and the consumers are reading messgaes from topic.
This lends to very efficient implementations because what the underlying ntework infrastructure can do is it can do baching. That is instead of sending messgaes one at a time, it groups them together. and also the implementation of all this infrastructure can be spread across large numbersof noded in a data center that are referred to as brokers and they can also partition the topics among themselves to allow higher throughput and performance.

A key advantage of of this approach is that publishers  need not be aware of which processes are the subscribers, and vice-versa.A nother advanatage is that it lends otself to very efficeint implementation beacuse it can enable a numnber of communication optimizations, which include batching and topic partitioning across broker nodes. Yet another advantage is improved reliability, beacause broker nodes can replicate messages in a topic, so that if one node hosting a topic fails, the entire publicsh subscribe system cam continue execution with another node that contains a copy of all messages in that topic.

To become a publisher, a process simply needs to create a KafkaProducer object. and use it to perform send() operations to designated topics. Likewise to become a consumer, a process needs to create a KafkaConsumer object, whicj can then  be used to subscribe to topics of interest. The consumer then performs  repeated poll() operations, each of which returns a batch of messages from the requested topics. Kafka is commonly used as to produce input for, or receieve output from, MapReduce systems Such as Hadoop or Spark. 


How we can use sockets to implement a basic server.
Implement file server using Sockets:
Usually you avoid infinite loops but in server programs, you often have a spin loop that spins repeatedly to accept requests.
1. Accept the socket.
2. Start accepting requests.(To do this create input stream form the socket).
3 Based on that create inputstreamreader them we can also get bufferreader from the ImoutStreamReader, once we have that we can start    reading request
4. Read the first line and check if its a GET request for a file, make sure that the line is not null and the line starts with GET
5. Create a full path and concatenate with the path in the GET operation and now we are ready to process the file that we need. to do so we have to create the output stream based on the socket.
6. We cam create a new printwriter for the output stream.
7.check ifthe path we constructeed is a proper filea and the write the contents of the file.
8. Print 404 error message if the file was not found.

Implementing web servers is easy. how to get started using basic socket APIs and this will give you foundation to implement web servers
in the future for cloud computing.

























