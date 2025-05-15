# Kafka Lab in GitHub Codespaces (Group-Based)

This Kafka lab is designed for group-based learning. Learners will collaboratively install Kafka, create a topic, and develop producers and consumers in Python using `kafka-python`.

---

## 👥 Group Lab Structure

Each group will:
1. **Fork this repository** to their own GitHub account.
2. **Open it in GitHub Codespaces**.
3. Follow the notebook and README to:
   - Install Kafka (Docker Compose)
   - Set up topics
   - Create producers and consumers
   - Optionally integrate open data sources

---

## 🛠 Setup Instructions

### 1. Open Codespaces
After forking, open the repo in GitHub Codespaces. The devcontainer will:
- Start Kafka + Zookeeper via Docker Compose
- Set up Python environment with required packages

### 2. Kafka Services
Kafka runs locally in the Codespace at `localhost:9092`. Zookeeper runs on `2181`.

To check the services:
```bash
docker ps
```

---

## 🧪 Part 1: Create a Kafka Topic

Use the CLI to create a topic named `group-topic`:

```bash
docker exec -it kafka bash
kafka-topics --create --topic group-topic --bootstrap-server localhost:9092 --partitions 1 --replication-factor 1
```

You can also list topics:
```bash
kafka-topics --list --bootstrap-server localhost:9092
```

---

## ✍️ Part 2: Create a Producer (Python)

```python
from kafka import KafkaProducer
producer = KafkaProducer(bootstrap_servers='localhost:9092')
producer.send('group-topic', b'Hello from Producer!')
producer.flush()
```

---

## 📥 Part 3: Create a Consumer (Python)

```python
from kafka import KafkaConsumer
consumer = KafkaConsumer('group-topic', bootstrap_servers='localhost:9092', auto_offset_reset='earliest')
for msg in consumer:
    print(msg.value.decode())
    break
```

---

## 🌐 Part 4 (Optional): Connect to External/Open Producers

Try connecting to streaming APIs (e.g., Twitter, weather feeds) and send that data into Kafka.

Example extension:
- Use `requests` or `tweepy` to pull data
- Transform it in Python
- Push it to Kafka topic using the producer

---

## ✅ Tips for Groups

- Each group can create their own topic (`team1-topic`, `weather-feed`, etc.)
- Make sure Kafka is running before using Python clients
- Use print statements to debug message flow