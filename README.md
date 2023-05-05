# Multi-Threaded-Ticket-Sellers

I have implemented a program in C that will simulate ticket sellers selling concert tickets simultaneously in one hour using Pthread library to create threads and mutex.

## Summary : 
Ten customer queues with N customers are created at the start of the program. These queues keep track of the customer number, arrival time, and service time, which are all created at random. All arrival and service times are measured in minutes, with all customers arriving at the start of each minute. After that, each seller is given a customer queue and proceeds to process each consumer as they arrive. Each of the ten sellers is also assigned a type: L, M, or H. They will serve their customers faster or slower depending on their type, and will look for different seats in different ways. When a seller starts serving a customer, it will search for an open seat based on the seller type. An unlocked mutex indicates an open seat. This assures that each seat may only be claimed by one seller. Once a seller has successfully claimed a seat mutex, they will record certain information at that place, such as response time, turnaround time, and the type of seller that sold the seat. Until all seats are occupied or an hour has gone, all customers will be treated in the same manner. Any customers who were not able to be served would be turned away. All of the sold seats are gone through at the end of the simulation time, and the average response time, turn-around time, and throughput for each type of seller are calculated.

All of the functions share the total number of customers per seller, the global clock counter, pthread inputs, and seat specific structure variables. I have built our task using the code provided in the preview by simulating clock ticks in the main thread and controlling important regions and the sell process in the child threads dedicated to simulating ticket sales. In our project, we used the main thread to generate clock ticks in order to simulate a one-minute period of time.

I had the following presumption for the simulation:
1. State of seller's thread: In any given time quanta, each seller's thread is expected to be in the following state.
• Waiting: Waiting for new client
• Serving: Serving new client from the vender's line
• Processing: Processing and setting aside effort to process the sell.
• Completing: Completing sell for the client.  

2. Clock Tick: Lowest time that can be measured is one minute, and each child thread is designed to imitate one minute of work. Serving clients, for example, or believing that they would complete the sale.
3. To keep up time synchronization, new clock is generated.
4. A 2-dimensional matrix was used to represent a concert seat, with the expectation that only one thread would use the matrix, avoiding any seat assignment dispute.

I also calculated Average Response Time, Average Turnaround Time & Throughput which came out to be:

|   | Average Response Time | Average Turnaround Time | Throughput |
| ------------- | ------------- | ---- | ----| 
| H | 0.000000 | 32.60 | 0.08 |
| L | 0.466667 | 30.17 | 0.25 |
| M | 0.733333 | 29.27 | 0.47 |
