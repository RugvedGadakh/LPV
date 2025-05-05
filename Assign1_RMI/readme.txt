Step 1) Open terminal in the same path where code is stored.
Step 2) javac *.java
Step 3) rmiregistry
Step 4) Open new terminal and put command: java Server
Step 5) Open new terminal and put command: java Client

Explanaation:

✅ Summary of the Assignment:
📌 Purpose:
To demonstrate Java RMI, allowing a client to invoke remote methods (Addition, Subtraction, Multiplication, Division) on a remote server.

🧩 Key Components:
ServerIntf.java – Interface defining remote methods.

ServerImpl.java – Actual implementation of methods.

Server.java – Binds the remote object to the RMI registry.

Client.java – Client that calls the remote methods via RMI.

🎯 Key Concepts for Viva:
1. What is RMI?
RMI stands for Remote Method Invocation, a Java API that allows an object residing in one JVM (server) to invoke methods on an object in another JVM (client).

2. Why use interfaces in RMI?
The interface (ServerIntf) defines the contract (methods) that the server will implement and the client will use. It extends java.rmi.Remote, indicating it can be used remotely.

3. Why does every method throw RemoteException?
Remote method calls can fail due to network issues. Declaring throws RemoteException ensures that such scenarios are properly handled.

4. What is UnicastRemoteObject?
It is a base class that allows creation of remote objects. It handles the communication setup between client and server.

5. What does Naming.rebind("Server", serverImpl); do?
It registers the object serverImpl with the name "Server" in the RMI registry, so the client can look it up by this name.

6. What is Naming.lookup("rmi://localhost/Server")?
It is used by the client to get a reference to the remote object (proxy/stub) registered with the name "Server".

7. What if the server isn't running?
The client will throw a RemoteException or NotBoundException during lookup, as the object is not found in the RMI registry.

🤔 Common Viva Questions with Answers:
Q1. What are the steps involved in setting up RMI?
A:

Define a remote interface.

Implement the interface in a class extending UnicastRemoteObject.

Register the implementation with the RMI registry.

Lookup the remote object from the client and invoke methods.

Q2. Why is the ServerImpl constructor declared to throw RemoteException?
A: Because UnicastRemoteObject’s constructor can throw RemoteException.

Q3. What will happen if we don’t handle division by zero properly?
A: It could lead to ArithmeticException or unexpected behavior. Right now, your code prints a message but still tries to divide by zero. You should return a meaningful error or throw an exception.

Q4. What is the role of rmiregistry?
A: It's a name registry for RMI objects. It must be started before the server to allow object binding and lookup.

🔧 Suggested Improvements:
In Division() method, you should avoid dividing after printing the error:

java
Copy
Edit
if(num2 != 0){
    return num1 / num2;
} else {
    throw new RemoteException("Cannot divide by zero");
}
📝 Short Note You Can Use in Exam:
This RMI-based application consists of a client and a server. The client uses Naming.lookup() to access a remote object registered by the server. The server defines and implements arithmetic operations and binds them in the RMI registry using Naming.rebind(). This model demonstrates the distributed nature of Java RMI, where method invocation occurs over the network between different JVMs.
