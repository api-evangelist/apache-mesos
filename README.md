# Apache Mesos (apache-mesos)
Apache Mesos is a retired cluster manager (now in the Apache Attic) that provided efficient resource isolation and sharing across distributed applications or frameworks. It abstracted CPU, memory, storage, and other compute resources from machines, enabling fault-tolerant and elastic distributed systems. Mesos exposed comprehensive HTTP APIs for schedulers, operators, executors, and agents.

**URL:** [Visit APIs.json URL](https://raw.githubusercontent.com/api-evangelist/apache-mesos/refs/heads/main/apis.yml)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=company-api-evangelist&utm_content=repo)

## Tags:

 - Cluster Management, Distributed Systems, Resource Management, Retired, Scheduling

## Timestamps

- **Created:** 2026-03-16
- **Modified:** 2026-04-19

## APIs

### Apache Mesos Operator HTTP API
The Mesos Operator HTTP API provides a POST-based API at /api/v1 on both master and agent nodes for cluster administration including health checks, state queries, resource reservation, maintenance scheduling, quota management, and agent lifecycle management. Supports JSON and Protobuf encoding.

**Human URL:** [https://mesos.apache.org/documentation/latest/operator-http-api/](https://mesos.apache.org/documentation/latest/operator-http-api/)

#### Tags:

 - Cluster Management, HTTP API, Operations, Resource Management

#### Properties

- [Documentation](https://mesos.apache.org/documentation/latest/operator-http-api/)
- [GitHubRepository](https://github.com/apache/mesos)

### Apache Mesos Scheduler HTTP API
The Mesos Scheduler HTTP API at /api/v1/scheduler enables framework schedulers to subscribe to resource offers, launch tasks, kill tasks, reconcile status, and manage framework lifecycle over a persistent HTTP connection with RecordIO-encoded streaming responses.

**Human URL:** [https://mesos.apache.org/documentation/latest/scheduler-http-api/](https://mesos.apache.org/documentation/latest/scheduler-http-api/)

#### Tags:

 - Framework, HTTP API, Scheduling, Tasks

#### Properties

- [Documentation](https://mesos.apache.org/documentation/latest/scheduler-http-api/)
- [GitHubRepository](https://github.com/apache/mesos)

## Common Properties

- [Portal](https://mesos.apache.org/)
- [GitHubOrganization](https://github.com/apache)
- [GitHubRepository](https://github.com/apache/mesos)
- [Documentation](https://mesos.apache.org/documentation/latest/)
- [Blog](https://mesos.apache.org/blog/)
- [TermsOfService](https://www.apache.org/licenses/LICENSE-2.0)

## Features

| Name | Description |
|------|-------------|
| Resource Abstraction | Abstracts CPU, memory, storage, and other compute resources from physical machines across the entire cluster. |
| Two-Level Scheduling | Framework schedulers receive resource offers from Mesos and decide how to use them, enabling coexistence of diverse workloads. |
| Linear Scalability | Proven to scale to tens of thousands of nodes with fault-tolerant replicated master using ZooKeeper. |
| Container Support | Native Docker and AppC container image support for running containerized workloads. |
| HTTP API | Comprehensive HTTP API supporting JSON and Protobuf encoding for schedulers, operators, executors, and agents. |
| High Availability | Fault-tolerant master failover via ZooKeeper with automatic leader election and state recovery. |
| Resource Reservations | Static and dynamic resource reservations for frameworks and roles with quota management. |
| Maintenance Scheduling | Built-in maintenance window scheduling for graceful draining and reactivation of agent nodes. |

## Use Cases

| Name | Description |
|------|-------------|
| Distributed Systems Orchestration | Run multiple distributed frameworks including Hadoop, Spark, and Kafka on shared cluster resources. |
| Container Orchestration | Schedule and manage containerized workloads across a datacenter with resource isolation. |
| Big Data Processing | Run Apache Spark, Hadoop MapReduce, and other big data frameworks on Mesos-managed resources. |
| Microservices Platform | Host microservices workloads with Marathon framework providing long-running service scheduling on Mesos. |

## Integrations

| Name | Description |
|------|-------------|
| Apache Hadoop | Run Hadoop MapReduce jobs on Mesos-managed cluster resources. |
| Apache Spark | Apache Spark supports Mesos as a cluster manager for distributed job execution. |
| Apache Kafka | Kafka brokers can be scheduled and managed on Mesos clusters. |
| Apache ZooKeeper | ZooKeeper provides leader election and state storage for Mesos master high availability. |
| Docker | Native Docker container image and runtime support for containerized workload execution. |
| Elasticsearch | Elasticsearch can be deployed and managed as a framework on Mesos clusters. |

## Maintainers

**FN:** Kin Lane

**Email:** info@apievangelist.com
