---
layout: post
title:  "Apache Flink"
date:   2022-11-25 22:58:30
categories: jekyll update
tags: featured
image: /assets/article_images/2014-08-29-welcome-to-jekyll/desktop.JPG
---
# Apache Flink

Apache Flink is a distributed stream processor with intuitive and expressive API’s to implement stateful stream processing applications. Stream processing is becoming more popular because it provides superior solutions for many established use cases such as ETL and transactional pipelines.

# Introduction to Stateful Stream Processing

Data and data processing have been omnipresent in businesses for many decades. The typical architecture most businesses implement distinguishes two types of data processing: transactional and analytical. 

## Transactional Processing

Companies use all kinds of applications for day to day business activities, such as enterprise resource planning (ERP) systems, customer relationship management (CRM) software and web based applications. These applications are typically designed with separate tiers for data processing and storage

  

![Untitled](flink_images/Untitled.png)

This application design can cause problems when applications need to evolve or scale, so changing the schema of a table or scaling a database system requires careful planning and a lot of effort. A recent approach around this is the microservices design pattern. Microservices are designed as small, self-contained and independent applications. More complex applications are built by connecting several microservices with each other that only communicate over well-defined interfaces. 

![Untitled](flink_images/Untitled%201.png)

## Analytics Processing

The data that is stored in various transactional database systems of a company can provide valuable insights about a company’s business operations. However, transactional data is often distributed across several disconnected database systems and is more valuable when it can be jointly analysed. This is where datawarehouses come in, with ETL processes being used to transofrm it into a common representation. 

![Untitled](flink_images/Untitled%202.png)

## Stateful Stream Processing

Virtually all data is created as a continuous stream of events. Stateful stream processing is an application design pattern for processing unbounded streams of events and is applicable to many different use-cases in the IT infrastructure of a company. 

Any application that processes a stream of events and does not just perform trivial record-at-a-time transformations needs to be stateful, with the ability to store and access intermediate data. Apache flink stores the application state locally in memory or in an embedded database. Flink guarantees fault tolerance by periodically writing a consistent checkpoint of the application state to a remote and durable storage. 

![Untitled](flink_images/Untitled%203.png)

Stateful stream processing applications often ingest their incoming events from an event log. An event log stores and distributes event streams. Event logs are append-only, so are published to all consumers in exactly the same order. There are three main classes of applications that are commonly implemented using stateful stream processing

### Event-driven applications

Event-driven applications are stateful streaming applications that ingest event streams and process the events with application specific business-logic. These apps can trigger actions such as sending an alert to an outgoing stream event to be consumed by another app. 

Some common use cases include:

- real-time recommendations
- pattern detection or complex event processing
- anomaly detection

They are an evolution of microservices, in that they communicate via event logs instead of REST calls and hold application data as local state instead of writing/reading from an external data store. 

![Untitled](flink_images/Untitled%204.png)

## Data Pipelines

A traditional approach to synchronize data in different storage systems is periodic ETL jobs. However, they do not meet the latency requirements for many of today’s use cases. An alternative is to use an event log to distribute updates. Ingesting, transforming and inserting data with low latency is another common use case for stateful stream processing applications. This is known as a data pipeline, a stream processor that operates a data pipeline should also feature may source and sink connectors to read/write from various storage systems. 

## Streaming Analytics

ETL jobs periodically import data into a datastore and the data is processed by adhoc or scheduled queries. A streaming analytics application continuously ingests streams of events and updates its results by incorporateing the latest events with low latency. 

Typically, streaming apps store their result in an external data store that supports efficient updates such as a database or key-value store. The live updated results of a streaming analytics application can be used to power dashboard applications. 

![Untitled](flink_images/Untitled%205.png)

# Introduction to Dataflow Programming

A dataflow program describes how data flows between operations. Dataflow programs are commonly represented as directed graphs where nodes are called operators, and edges represent data dependencies.