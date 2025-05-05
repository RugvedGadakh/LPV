javac Bully.java
java Bully
javac Ring.java
java Ring


Explanation: 

 Purpose:
To elect a coordinator (leader) in a distributed system when a higher-priority process is available.

📘 Key Concepts:
Higher process IDs have higher priority.

A process detects coordinator failure and initiates election.

It sends election messages to all higher-numbered processes.

If no response → it becomes the coordinator.

If a higher process responds → it takes over election.

▶️ Sample Output:

Bully Algorithm
1. Create processes
Enter the number of processes:- 5
P1 created
P2 created
P3 created
P4 created
P5 created
Process P5 is the coordinator
4. Down a process
Enter the process number to down:- 5
Process 5 is down.
5. Run election algorithm
Enter the process number which will perform election:- 3
Election message sent from process 3 to process 4
Election message sent from process 3 to process 5
Election message sent from process 4 to process 5

✅ Viva Questions – Bully Algorithm:

Q1: Why is it called the "Bully" algorithm?
A: Because higher-numbered processes "bully" lower ones by taking control of the coordinator role.

Q2: Who initiates the election?
A: Any process that detects the coordinator is down.

Q3: What if two processes initiate an election at the same time?
A: The process with the higher ID will eventually become the coordinator.

Q4: Is the Bully algorithm synchronous or asynchronous?
A: Typically considered synchronous, but can be adapted.

Q5: Time Complexity?
A: Worst-case: O(n) messages sent in the system.

✅ 2. Ring Algorithm – Explanation
📌 Purpose:
To elect a coordinator using ring topology where messages are passed in a circular fashion.

📘 Key Concepts:
All processes are in a logical ring.

Initiator sends its ID around the ring.

Each process adds its ID and forwards.

Highest ID becomes the new coordinator.

▶️ Sample Output:

Ring Algorithm
1. Create processes
Enter the total number of processes:- 5
P1 created.
P2 created.
P3 created.
P4 created.
P5 created.
P5 is the coordinator

4. Down a process
Enter the process to down:- 5
Process P5 is down.

5. Run election algorithm
Enter the process which will initiate election:- 3
Process P3 sending the following list:- [ 3 ]
Process P4 sending the following list:- [ 3 4 ]
Process P1 sending the following list:- [ 3 4 1 ]
Process P2 sending the following list:- [ 3 4 1 2 ]
Process P3 has declared P4 as the coordinator

✅ Viva Questions – Ring Algorithm:

Q1: What happens if the initiator is the only active process?
A: It declares itself the coordinator.

Q2: Why do we use a circular list in Ring Algorithm?
A: To simulate ring topology where every node has exactly one successor.

Q3: How is the new coordinator selected?
A: The highest process ID in the list becomes the coordinator.

Q4: How does the ring algorithm avoid conflicts?
A: Only one token/message passes around the ring, no broadcast.

Q5: Time Complexity?
A: O(n) messages — one complete round of the ring.