# Quick Start for Bare Metal/VM installs
This document explains installation of Luna Streaming for Bare Metal/VM deployments with a Pulsar tarball. 
The resulting Luna Streaming deployment includes: 
  - Tiered Storage: Offload historical messages to more cost effective object storages such as AWS S3, Azure Blob, Google Cloud Storage, and HDFS.
  - Built-in Schema Registry: Guarantee messaging type safety on a per-topic basis without relying on any external facility.
  - Pulsar I/O connectors: Enables Pulsar to exchange data with external systems, either as sources or sinks.
  - Pulsar Function: Lightweight compute extensions of Pulsar brokers which enable real-time simple event processing within Pulsar.
  - Pulsar SQL: SQL-based interactive query for message data stored in Pulsar.
  - Pulsar Transactions: enables event streaming applications to consume, process, and produce messages in one atomic operation.

## Requirements
  - A Linux server or VM
  - JDK 11
    Pulsar can run with JDK8, but DataStax Luna Streaming is designed for Java 11. Java 17 LTS will be supported in the future.
  - File System
    DataStax recommends XFS, but ext4 will work
  - For a single node install, a server with at least 8 CPU and 32 GB of memory is required
  - For a small high-availability server, 4 servers are required. The servers must be on the same network so they can communicate with each other.
  - Servers should have at least 50 GB in their root disk volume.
  - BookKeeper should use one volume device for the journal, and one volume device for the ledgers. The journal device should be 20GB. The ledger volume device should be sized to hold the expected amount of stored message data.
  - DataStax recommends a separate data disk volume for ZooKeeper.
  - Operating System Settings Disable Swap and set Linux Transparent Huge Pages (THP) to madvice. Check this setting with cat /sys/kernel/mm/transparent_hugepage/enabled and cat /sys/kernel/mm/transparent_hugepage/defrag
