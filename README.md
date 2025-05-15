# Kafka Lab with Confluent Cloud (Codespaces Compatible)

This project connects to a hosted Kafka cluster (Confluent Cloud) using Python and `kafka-python`.

## Setup

1. Sign up at [https://confluent.cloud](https://confluent.cloud)
2. Create a Kafka cluster and topic (e.g., `group-topic`)
3. Go to **Clients > Python** to get your connection details
4. Copy `.env.example` to `.env` and fill in your credentials
5. Open this repo in Codespaces

## Run the Notebook

1. Open `notebooks/kafka_confluent_demo.ipynb`
2. Run the cells to:
   - Connect to Confluent Cloud
   - Send a message to Kafka
   - Read the message back