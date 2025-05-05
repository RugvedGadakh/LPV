Step 1) javac Tring.java
Step 2) Tring.java
Step 3) Number of nodes in ring: 10
Step 4) Sender: 4 Receiver: 8
Step 5) Data to send: 80

Explanation:

✅ Summary of the Program:
📌 Purpose:
To simulate token passing in a token ring network for controlled communication between nodes.

🔍 How It Works:

User Inputs:

Number of nodes in the ring.

Sender node ID.

Receiver node ID.

Data to send.

Simulation:

Token is passed from Node 0 to the sender.

Sender then starts forwarding the data node by node until it reaches the receiver.

Finally, the receiver prints that it has received the data.

🧠 Key Concepts Covered:
🔸 Token Ring Protocol:
A media access control protocol where a token (a special data frame) is passed around the ring. A node can send data only when it has the token, ensuring collision-free communication.

📌 Sample Output:

Enter Number Of Nodes You Want In The Ring : 5
Ring Formed Is As Below: 
0 1 2 3 4 
0
Enter Sender : 2
Enter Receiver : 4
Enter Data To Send : 50
Token Passing :  0-> 1-> 2
Sender:2 Sending Data: 50
Data: 50 Forwarded By: 2
Data: 50 Forwarded By: 3
Receiver: 4 Received The Data: 50
📘 Viva Questions and Answers:
🔹 Q1. What is the Token Ring protocol?
A:
It's a network protocol in which a token circulates around the ring. A node must acquire the token to send data, ensuring collision-free and sequential transmission.

🔹 Q2. Why do we use modulus %n in the loop?
A:
To simulate the circular nature of the ring. When the index reaches the end, it wraps around to 0 using i = (i+1)%n.

🔹 Q3. What happens if the sender and receiver are the same?
A:
The data loop will not forward to any other node, and the receiver (same as sender) receives the data directly.

🔹 Q4. Can the program handle multiple rounds of communication?
A:
Yes. The do-while loop allows multiple rounds of data transmission until the user chooses to exit by entering 0.

🔹 Q5. What does the "token" variable represent in this code?
A:
It represents the current holder of the token. Initially, it’s 0. It is updated to the last sender at the end of each round.

📝 Notes for Assignment:
This Java program simulates a Token Ring protocol using a loop and modulo operation to represent the ring topology. Data transfer is controlled using a virtual token, ensuring only one node sends data at a time, just like in real token ring networks.