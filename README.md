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



