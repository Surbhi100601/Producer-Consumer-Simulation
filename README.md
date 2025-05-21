# Producer-Consumer-Simulation
Create three processes representing 3 producers. Create 10 processes representing 10 consumers. 
Make a list of products which will be distributed to the consumers. The producers can stock maximum 
5 nos of each product. You may decide which producer will stock which product. The consumers will 
randomly visit the producers to get the products. Simulate the behaviour by introducing random 
delays in the consumers visits to the producers. The consumer can visit any producer for getting the 
product that it wants. Each Producer keeps a record of how many quantity of each product is 
remaining and when the quantity becomes zero, the producer will stock it back to 5 after a random 
delay. The main program should allow the user to check status of each producer and consumer at any 
point of time. Use suitable IPC for consumer requesting a product to a producer and producer either 
giving the product or rejecting the request. 
# LOGIC –  
• Shared memory to store product stock and a termination flag. 
• Named pipes (FIFOs) for communication between producers and consumers. 
• Multiple producers manage stock of 3 products: Laptop, Computer, CPU. 
• Consumers randomly request products from producers. 
• Producers fulfill requests if stock is available, otherwise restock after depletion. 
• The main process monitors the system, displays stock (status), and stops execution (exit). 
# Algorithm for Main Process - 
1. Create shared memory (shmget) and attach it (shmat). 
2. Initialize stock of all products to MAX_STOCK. 
3. Create FIFOs for each producer (request FIFOs) and a common response FIFO. 
4. Fork producer processes (NUM_PRODUCERS times). 
o Each child runs producer_process(i). 
5. Fork consumer processes (NUM_CONSUMERS times). 
o Each child runs consumer_process(i). 
6. In a loop, wait for user input: 
o If status, print stock. 
o If exit, set terminate = 1, wait, and break loop. 
7. Clean up: remove shared memory and delete FIFOs. 
# Algorithm for Producer Process 
1. Open the corresponding request FIFO in read-only mode. 
2. Repeat: 
o If terminate is set in shared memory, exit. 
o Read a request: contains producer_id, product_id, quantity. 
o If enough stock, reduce it and prepare success message. 
o Else, send out-of-stock message. 
o Write response to the response FIFO. 
o If stock is 0 for that product: 
▪ Sleep (2–4 seconds). 
▪ Refill to MAX_STOCK. 
# Algorithm for Consumer Process 
1. Repeat: 
o If terminate is set in shared memory, exit. 
o Sleep randomly (1–3 seconds). 
o Choose random producer, product, and quantity. 
o Open producer's request FIFO in write mode and send request. 
o Open response FIFO in read mode and read the response. 
o Print the received m
