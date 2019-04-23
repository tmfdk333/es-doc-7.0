# [Elasticsearch Reference: 7.0](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html)

## [1] Getting started(6)
### 1-1. Basic Concepts
### 1-2. Installation
### 1-3. Exploring Your Cluster(5)
### 1-4. Modifying Your Data(3)
### 1-5. Exploring Your Data(5)
### 1-6. Conclusion

## [2] Set up Elasticsearch(13)
### 2-1. Installing Elasticsearch(6)
### 2-2. Configuring Elasticsearch(12)
### 2-3. Important Elasticsearch configuration(10)
### 2-4. Important System Configuration(7)
### 2-5. Bootstrap Checks(15)
### 2-6. Starting Elasticsearch
### 2-7. Stopping Elasticsearch
### 2-8. Adding nodes to your cluster
### 2-9. Set up X-Pack
### 2-10. Configuring monitoring(3)
### 2-11. Configuring security(13)
### 2-12. Configuring X-Pack Java Clients
### 2-13. Bootstrap Checks for X-Pack

## [3] Upgrade Elasticsearch(3)
### 3-1. Rolling upgrades
### 3-2. Full cluster restart upgrade
### 3-3. Reindex before upgrading(2)

## [4] API conventions(4)
### 4-1. Multiple Indices
### 4-2. Date math support in index names
### 4-3. Common options
### 4-4. URL-based access control

## [5] Document APIs(14)
### 5-1. Reading and Writing documents
### 5-2. Index API
### 5-3. Get API
### 5-4. Delete API
### 5-5. Delete By Query API
### 5-6. Update API
### 5-7. Update By Query API
### 5-8. Multi Get API
### 5-9. Bulk API
### 5-10. Reindex API
### 5-11. Term Vectors
### 5-12. Multi termvectors API
### 5-13. "?refresh"
### 5-14. Optimistic concurrency control

## [6] Search APIs(14)
### 6-1. Search
### 6-2. URI Search
### 6-3. Request Body Search(23)
### 6-4. Search Template
### 6-5. Multi Search Template
### 6-6. Search Shards API
### 6-7. Suggesters(5)
### 6-8. Multi Search API
### 6-9. Count API
### 6-10. Validate API
### 6-11. Explain API
### 6-12. Profile API(3)
### 6-13. Field Capabilities API
### 6-14. Ranking Evaluation API

## [7] Aggregations(8)
### 7-1. Metrics Aggregations(16)
### 7-2. Bucket Aggregations(24)
### 7-3. Pipeline Aggregations(15)
### 7-4. Matrix Aggregations(1)
### 7-5. Caching heavy aggregations
### 7-6. Returning only aggregation results
### 7-7. Aggregation Metadata
### 7-8. Returning the type of the aggregation

## [8] Indices APIs(25)
### 8-1. Create Index
### 8-2. Delete Index
### 8-3. Get Index
### 8-4. Indices Exists
### 8-5. Open / Close Index API
### 8-6. Shrink Index
### 8-7. Split Index
### 8-8. Rollover Index
### 8-9. Put Mapping
### 8-10. Get Mapping
### 8-11. Get Field Mapping
### 8-12. Types Exists
### 8-13. Index Aliases
### 8-14. Update Indices Settings
### 8-15. Get Settings
### 8-16. Analyze(1)
### 8-17. Index Templates
### 8-18. Indices Stats
### 8-19. Indices Segments
### 8-20. Indices Recovery
### 8-21. Indices Shard Stores
### 8-22. Clear Cache
### 8-23. Flush(1)
### 8-24. Refresh
### 8-25. Force Merge

## [9] cat APIs(18)
### 9-1. cat aliases
### 9-2. cat allocation
### 9-3. cat count
### 9-4. cat fielddata
### 9-5. cat health
### 9-6. cat indices
### 9-7. cat master
### 9-8. cat nodeattrs
### 9-9. cat nodes
### 9-10. cat pending tasks
### 9-11. cat plugins
### 9-12. cat recovery
### 9-13. cat repositories
### 9-14. cat thread pool
### 9-15. cat shards
### 9-16. cat segments
### 9-17. cat snapshots
### 9-18. cat templates

## [10] Cluster APIs(15)
### 10-1. Cluster Health
### 10-2. Cluster State
### 10-3. Cluster Stats
### 10-4. Pending cluster tasks
### 10-5. Cluster Reroute
### 10-6. Cluster Update Settings
### 10-7. Cluster Get Settings
### 10-8. Nodes Stats
### 10-9. Nodes Info
### 10-10. Nodes Feature Usage
### 10-11. Remote Cluster Info
### 10-12. Task Management API
### 10-13. Nodes hot_threads
### 10-14. Cluster Allocation Explain API
### 10-15. Voting Configuration Exclusions

## [11] Query DSL(11)
### 11-1. Query and filter context
### 11-2. Match All Query
### 11-3. Full text queries(8)
### 11-4. Term level queries(11)
### 11-5. Compound queries(5)
### 11-6. Joining queries(4)
### 11-7. Geo queries(4)
### 11-8. Specialized queries(6)
### 11-9. Span queries(9)
### 11-10. Minimum Should Match
### 11-11. Multi Term Query Rewrite

## [12] Mapping(5)
### 12-1. Removal of mapping types
### 12-2. Field datatypes(22)
### 12-3. Meta-Fields(8)
### 12-4. Mapping parameters(26)
### 12-5. Dynamic Mapping(2)

## [13] Analysis(7)
### 13-1. Anatomy of an analyzer
### 13-2. Testing analyzers
### 13-3. Analyzers(10)
### 13-4. Normalizers
### 13-5. Tokenizers(15)
### 13-6. Token Filters(49)
### 13-7. Character Filters(3)

## [14] Modules(14)
### 14-1. Discovery and cluster formation(8)
### 14-2. Shard allocation and cluster-level routing(5)
### 14-3. Local Gateway(1)
### 14-4. HTTP
### 14-5. Indices(7)
### 14-6. Network Settings
### 14-7. Node
### 14-8. Plugins
### 14-9. Scripting(6)
### 14-10. Snapshot and Restore
### 14-11. Thread Pool
### 14-12. Transport
### 14-13. Remote clusters
### 14-14. Cross-cluster search

## [15] Index modules(9)
### 15-1. Analysis
### 15-2. Index Shard Allocation(4)
### 15-3. Mapper
### 15-4. Merge
### 15-5. Similarity module
### 15-6. Slow Log
### 15-7. Store(1)
### 15-8. Translog
### 15-9. Index Sorting(1)

## [16] Ingest node(6)
### 16-1. Pipeline Definition
### 16-2. Ingest APIs(4)
### 16-3. Accessing Data in Pipelines
### 16-4. Conditional Execution in Pipelines(4)
### 16-5. Handling Failures in Pipelines
### 16-6. Processors(28)

## [17] Managing the index lifecycle(8)
### 17-1. Getting started with index lifecycle management
### 17-2. Policy phases and actions(4)
### 17-3. Set up index lifecycle management policy(2)
### 17-4. Using policies to manage index rollover(1)
### 17-5. Update policy(3)
### 17-6. Index lifecycle error handling
### 17-7. Restoring snapshots of managed indices
### 17-8. Start and stop index lifecycle management

## [18] SQL access(18)
### 18-1. Overview
### 18-2. Getting Started with SQL
### 18-3. Conventions and Terminology(1)
### 18-4. Security
### 18-5. SQL REST API
### 18-6. SQL Translate API
### 18-7. SQL CLI
### 18-8. SQL JDBC(1)
### 18-9. SQL ODBC(2)
### 18-10. SQL Client Applications(10)
### 18-11. SQL Language
### 18-12. Lexical Structure
### 18-13. SQL Commands(5)
### 18-14. Data Types
### 18-15. Index patterns
### 18-16. Functions and Operators(13)
### 18-17. Reserved keywords
### 18-18. SQL Limitations

## [19] Monitoring Elasticsearch(3)
### 19-1. Collectors
### 19-2. Exporters(2)
### 19-3. Pausing Data Collection

## [20] Rolling up historical data(6)
### 20-1. Overview
### 20-2. API Quick Reference
### 20-3. Getting Started
### 20-4. Understanding Groups(2)
### 20-5. Rollup Aggregation Limitations
### 20-6. Rollup Search Limitations

## [21] Frozen indices(3)
### 21-1. Best practices
### 21-2. Searching a frozen index
### 21-3. Monitoring frozen indices

## [22] X-Pack APIs(13)
### 22-1. Info API
### 22-2. Cross-cluster replication APIs(11)
### 22-3. Explore API
### 22-4. Freeze index
### 22-5. Index lifecycle management API(10)
### 22-6. Licensing APIs(7)
### 22-7. Migration APIs(1)
### 22-8. Machine learning APIs(44)
### 22-9. Rollup APIs(9)
### 22-10. Security APIs(25)
### 22-11. Unfreeze index
### 22-12. Watcher APIs(10)
### 22-13. Definitions(9)

## [23] Command line tools(9)
### 23-1. elasticsearch-certgen
### 23-2. elasticsearch-certutil
### 23-3. elasticsearch-migrate
### 23-4. elasticsearch-node
### 23-5. elasticsearch-saml-metadata
### 23-6. elasticsearch-setup-passwords
### 23-7. elasticsearch-shard
### 23-8. elasticsearch-syskeygen
### 23-9. elasticsearch-users

## [24] How To(5)
### 24-1. General recommendations
### 24-2. Recipes(3)
### 24-3. Tune for indexing speed
### 24-4. Tune for search speed(3)
### 24-5. Tune for disk usage

## [25] Testing(1)
### 25-1. Java Testing Framework(6)