Terminal 1:

python client.py

Terminal 2:

python server.py

Explanation:

✅ Summary of the Assignment:
📌 Goal:
To implement a centralized time synchronization system where a master server (clock) synchronizes all connected clients' clocks using average time difference.

🔍 How It Works:
Client (client.py):
Sends its local time to the server every 5 seconds.

Receives a synchronized time from the server based on calculated average.

Server (server.py):
Maintains a record (client_data) of all connected clients, their clock times, and time differences.

Periodically (every 5 sec):

Calculates average clock drift.

Sends adjusted/synchronized time to each client.

🔧 Key Concepts in This Assignment:
1. Berkeley Algorithm:
It is a centralized time synchronization technique:

The master polls all the clients for their time.

Computes the average time difference.

Sends back a new synchronized time to each client.

2. Time Drift Calculation:
clock_time_diff = datetime.now() - clock_time

This calculates how ahead/behind each client is from the server's time.

3. Threading in Python:
Used to handle multiple client connections and background synchronization concurrently.

Each client runs two threads:

One for sending time

One for receiving time

🎯 Viva Questions and Answers:
🔹 Q1. What is the purpose of this assignment?
A: To simulate clock synchronization in distributed systems using a central server (master node) and clients (slave nodes), inspired by Berkeley’s Algorithm.

🔹 Q2. How does the server determine synchronized time?
A:

It collects current times from all clients.

Calculates the average clock drift using getAverageClockDiff().

Adds that average to the current server time.

Sends this synchronized time back to all clients.

🔹 Q3. What is the role of threading here?
A:

It allows:

Multiple clients to send/receive time simultaneously.

Server to receive from clients and broadcast synchronized time in parallel.

🔹 Q4. What happens if a client disconnects?
A:
The try/except in synchronizeAllClocks() handles it — if sending to a client fails, it prints an error. You can improve this by removing the client from client_data.

🔹 Q5. How is this different from Cristian's Algorithm?
A:

Berkeley’s Algorithm is decentralized: It considers all clocks, not just the server's.

Cristian's Algorithm uses the server’s clock as the reference and assumes known network delay.

🔹 Q6. How is time sent between client and server?
A:
Time is serialized as a string using str(datetime.datetime.now()), and parsed back using dateutil.parser.

📝 Short Summary for Notes:
This program uses Berkeley’s Algorithm to synchronize time among distributed clients. Clients send their local time to a master server. The server calculates the average time difference and sends back the corrected time to all clients. This simulation uses Python’s socket and threading libraries to establish real-time communication and synchronization.
