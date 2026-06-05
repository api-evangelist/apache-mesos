# Apache Mesos (apache-mesos)

Apache Mesos is a retired cluster manager (now in the Apache Attic) that provided efficient resource isolation and sharing across distributed applications or frameworks. It abstracted CPU, memory, storage, and other compute resources from machines, enabling fault-tolerant and elastic distributed systems. Mesos exposed comprehensive HTTP APIs for schedulers, operators, executors, and agents.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/apache-mesos/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/apache-mesos/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Consumer
- **Access:** 3rd-Party

## Tags

- Cluster Management
- Distributed Systems
- Resource Management
- Scheduling
- Retired

## Timestamps

- **Created:** 2026-03-16
- **Modified:** 2026-05-19

## APIs

### Apache Mesos Operator HTTP API

The Mesos Operator HTTP API provides a POST-based API at /api/v1 on both master and agent nodes for cluster administration including health checks, state queries, resource reservation, maintenance scheduling, quota management, and agent lifecycle management. Supports JSON and Protobuf encoding.

- **Human URL:** [https://mesos.apache.org/documentation/latest/operator-http-api/](https://mesos.apache.org/documentation/latest/operator-http-api/)

#### Tags

- Cluster Management
- HTTP API
- Operations
- Resource Management

#### Properties

- [Documentation](https://mesos.apache.org/documentation/latest/operator-http-api/)
- [GitHub Repository](https://github.com/apache/mesos)
- [OpenAPI](openapi/apache-mesos-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/apache-mesos.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/apache-mesos.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Apache Mesos Scheduler HTTP API

The Mesos Scheduler HTTP API at /api/v1/scheduler enables framework schedulers to subscribe to resource offers, launch tasks, kill tasks, reconcile status, and manage framework lifecycle over a persistent HTTP connection with RecordIO-encoded streaming responses.

- **Human URL:** [https://mesos.apache.org/documentation/latest/scheduler-http-api/](https://mesos.apache.org/documentation/latest/scheduler-http-api/)

#### Tags

- Framework
- HTTP API
- Scheduling
- Tasks

#### Properties

- [Documentation](https://mesos.apache.org/documentation/latest/scheduler-http-api/)
- [GitHub Repository](https://github.com/apache/mesos)
- [Postman Collection](collections/apache-mesos.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/apache-mesos.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Portal](https://mesos.apache.org/)
- [GitHub Organization](https://github.com/apache)
- [GitHub Repository](https://github.com/apache/mesos)
- [Documentation](https://mesos.apache.org/documentation/latest/)
- [Blog](https://mesos.apache.org/blog/)
- [Terms of Service](https://www.apache.org/licenses/LICENSE-2.0)
- [Features](undefined)
- [Use Cases](undefined)
- [Integrations](undefined)

## Maintainers

**FN:** Kin Lane
**Email:** info@apievangelist.com
