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
