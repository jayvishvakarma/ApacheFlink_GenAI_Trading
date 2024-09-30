# **Building-a-Real-Time-Stock-Market-Data-Pipeline**
This project implements a real-time stock market data pipeline using Redpanda (Kafka), Apache Flink, GenAI, and the Alpaca API. It processes market data to generate trading signals and executes trades based on those signals.
Table of Contents
1.	Prerequisites
2.	Infrastructure Setup
3.	Microservices Architecture
4.	Workflow
5.	Configuration
6.	Dependencies
7.	Getting Started
8.	Testing
9.	Running Locally
10.	Interacting with Services
11.	Contributing
12.	License
13.	Additional Notes

## **1.	Prerequisites**
Before you begin, ensure you have met the following requirements:

•	Docker Desktop installed on your local machine.

•	Python 3.8+ installed for any additional scripting or testing.

•	An account with Alpaca for accessing the trading API.

## **2.	Infrastructure Setup**
The project is designed to run locally with Docker, using the following services:

•	Redpanda for Kafka message brokering.

•	Apache Flink for real-time data processing.

•	Alpaca API for trading execution.

•	Slack API for notifications.
           Docker Compose
           This project uses Docker Compose to manage services. Ensure you have the docker-compose.yml file in your project root
           
## **3.	Microservices Architecture**
![Architeccture](https://github.com/user-attachments/assets/940df9e2-2935-4c90-b930-25b7f8e2d9a6)

•	Kafka Producer: Publishes stock prices and news to Kafka topics.

•	Stream Processing Service: Analyzes data and generates trading signals.

•	Trading Signal Service: Generates trading signals based on market conditions.

•	Trade Execution Service: Executes trades via the Alpaca API.

•	Notification Service: Sends alerts to a Slack channel.

## **4.	Workflow**

![WorkFlow](https://github.com/user-attachments/assets/4059dba6-7430-43a6-816c-169985b5b629)

### **a.	Data Ingestion:**
	Fetch historical news and stock prices from the Alpaca API.
	Produce messages to respective Kafka topics in Redpanda.
### **b.	Stream Processing:**
	Use Apache Flink SQL to create tables and views for processing market news and stock prices.

	Calculate moving averages and generate trading signals.
### **c.	Trading Signal Handling:**
	Messages containing trading signals are sent to a Slack channel and executed as trades via the Alpaca API.

## **5.	Configuration**
•	Update the .env file with your Alpaca API key and secret, Slack webhook URL, and any other necessary configurations.

•	Ensure your Docker resources (CPU, Memory) are configured appropriately in Docker Desktop.

## **6.	Dependencies**
Make sure to install the following Python dependencies for any additional scripting:
pip install requests flask alpaca-trade-api slack_sdk
alpaca-trade-api
slack_sdk
       
## **7.	Getting Started**
To get started with the project, follow these steps:
1.	Clone the Repository:
https://github.com/jayvishvakarma/Building-a-Real-Time-Stock-Market-Data-Pipeline

3.	Build and Run Docker Containers: Use Docker Compose to build and start the services:
docker-compose up --build

## **8.	Testing**
To ensure all services are running correctly:

•	Check the logs:
docker-compose logs

## **9.	Running Locally**
Once the services are running, you can access:
•	**Flink Web UI:** http://localhost:8081 for monitoring Flink jobs.

![Flink Web UI](https://github.com/user-attachments/assets/1e8e960d-bdfe-42e4-9777-00a1ef558e6f)

•	**Redpanda UI:** Access the Redpanda UI to view topics and messages.
 
## **10.	Interacting with Services**
You can interact with the services using tools like curl or Postman. Here are some sample commands:
•	Send a test message to Kafka:
curl -X POST http://localhost:5000/api/send_message -H "Content-Type: application/json" -d '{"message": "Test message"}'

•	Check trading signals:
**curl http://localhost:5001/api/trading_signals**

![redPanda](https://github.com/user-attachments/assets/6d8fe44a-735a-424d-a7ca-2fa01e9837d5)


## **11.	License**
         All rights reserved. No copyright is allowed.
         
## **12.	Additional Notes**
•	Ensure your Docker Desktop has enough resources allocated (CPU, Memory).
•	For troubleshooting, refer to the logs of specific services using:
docker-compose logs 
•	For any issues related to the Alpaca API, refer to the Alpaca API documentation.
