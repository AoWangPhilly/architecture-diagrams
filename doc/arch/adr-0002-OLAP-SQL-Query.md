# ADR 2: Apache Druid for Lightning Fast OLAP SQL Queries

| Category   | Value            |
| ---------- | ---------------- |
| Identifier | adr-0002         |
| Status     | Accepted         |
| Author(s)  | Ao Wang          |
| Date:      | April 30th, 2024 |

**keywords:** Apache Druid, OLAP, SQL, Query, Tableau, PowerBI, Data Visualization

The driving force for influencing this design decision is boosting query processing times. Platforms such as Tableau and PowerBI are used to visualize data, but they need to query the data first. The longer the query time, the longer it takes to visualize the data. This will also result in more resources being used, which can lead to higher costs.

## Decision

We will utilize Apache Druid, an open-source, distributed, column-oriented OLAP database, for lightning-fast SQL queries. Druid is designed for sub-second query times, which is crucial for our platform. We will use Druid for our OLAP SQL queries, which will be used for visualizing data in Tableau and PowerBI.

## Rationale

Our platform ended up using Apache Druid because it's designed for its lightning fast query times and to handle high concurrency. Additionally, Druid is designed for real-time streaming ingestion and able to scale horizontally without performance degradation. This makes it the standout option for organizations that cannot afford to wait for batch processing cycles and need to make decisions based on the most current data available, which is crucial for our dashboarding platform.

Rejected Alternatives:

- DuckDB
  - DuckDB is an in-memory analytical database system that is designed for OLAP queries. It's designed for high performance and is able to handle complex queries.
  - However, DuckDB is not designed for real-time streaming ingestion, which is crucial for our platform. Additionally, DuckDB is not designed to scale horizontally, which is a requirement for our platform.
- SQLite
  - SQLite is a self-contained, serverless, zero-configuration, transactional SQL database engine. It's designed for simplicity and ease of use.
  - However, SQLite is not designed for OLAP queries and is not designed for high concurrency, which is a requirement for our platform.
- ClickHouse
  - ClickHouse is an open-source column-oriented database management system that allows generating analytical data reports in real-time.
  - However, ClickHouse is not designed for real-time streaming ingestion, which is crucial for our platform. Additionally, ClickHouse is not designed to scale horizontally, which is a requirement for our platform.

## Consequences

Some downsides to Apache Druid is that we primarily store data in Apache Parquet, which is a columnar storage format. Luckily, Druid is designed to work with columnar storage formats, so this is not a major issue, but Druid primarily works with Segments, which are immutable, time-ordered collections of data. Although we are able to ingest data in real-time and store the data as segments, this can lead to higher storage costs. Therefore, we'll need to transform the data from segments to Parquet files to reduce storage costs and if we want to do batch processing, we'll need to transform the data from Parquet files to segments. However, the benefits of Druid far outweigh the downsides, as we're in the business of providing lightning-fast OLAP SQL queries, which is crucial for our platform. This will help save money on storage.
