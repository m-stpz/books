# Message Queues

- Form of async service-to-service communication
  - used in serverless and microservices architecture
- Examples: Amazon SQS, Kafka, RabbitMQ
  - RabbitMQ: great for complex routing logic and traditional message queuing
  - Apache Kafka: designed for high-throughput, log-based streaming (Pub/Sub) where data needs to be replayed/retained
  - AWS SQS: Fully managed cloud-native queues

```
                            server
client -- uploads image -->  - resize ----> database
   ^                          - filter
   |                          - content moderation
   |                             |
   -------- response 6s later ---
```

## Core concepts

1. Producer: application/service that creates and sends the message
2. Queue: temporary storage folder/buffer that holds the message (either FIFO or priority sequence)
3. Consumer: application/service that connects to the queue, retrives the message, and processes it

### Sync vs. Async

1. Sync (HTTP/REST): service A calls service B and must wait for B to finish processing
   - If service B is slow or down, service A hangs or crashes

2. Async (Message queues): service A drops a message into the queue and moves on
   - Service B picks it up whenever possible

## Important considerations

1. Data consistency and idempotency: messages can sometimes be delivered twice
   - Consumers must be idempotent

2. Message ordering: the messages might be received out of order.
   - If order is important, we need to choose a queue that guarantees ordering
