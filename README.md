# [Elasticsearch Reference: 7.0](https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html)

## [1] Getting started
### 1-1. Basic Concepts
### 1-2. Installation
### 1-3. Exploring Your Cluster
#### 1-3-1) Cluster Health
#### 1-3-2) List All Indices
#### 1-3-3) Create an Index
#### 1-3-4) Index and Query a Document
#### 1-3-5) Delete an Index
### 1-4. Modifying Your Data
#### 1-4-1) Updating Documents
#### 1-4-2) Deleting Documents
#### 1-4-3) Batch Processing
### 1-5. Exploring Your Data
#### 1-5-1) The Search API
#### 1-5-2) Introducing the Query Language
#### 1-5-3) Executing Searches
#### 1-5-4) Executing Filters
#### 1-5-5) Executing Aggregations
### 1-6. Conclusion

## [2] Set up Elasticsearch
### 2-1. Installing Elasticsearch
#### 2-1-1) Install Elasticsearch from archive on Linux or MacOS
#### 2-1-2) Install Elasticsearch with ".zip" on Windows
#### 2-1-3) Install Elasticsearch with Debian Package
#### 2-1-4) Install Elasticsearch with RPM
#### 2-1-5) Install Elasticsearch with Windows MSI Installer
#### 2-1-6) Install Elasticsearch with Docker
### 2-2. Configuring Elasticsearch
#### 2-2-1) Setting JVM options
#### 2-2-2) Secure settings
#### 2-2-3) Logging configuration
#### 2-2-4) Auditing settings
#### 2-2-5) Cross-cluster replication settings
#### 2-2-6) Index lifecycle management settings
#### 2-2-7) License settings
#### 2-2-8) Machine learning settings
#### 2-2-9) Monitoring settings
#### 2-2-10) Security settings
#### 2-2-11) SQL access settings
#### 2-2-12) Watcher settings
### 2-3. Important Elasticsearch configuration
#### 2-3-1) "path.data" and "path.logs"
#### 2-3-2) "cluster.name"
#### 2-3-3) "node.name"
#### 2-3-4) "network.host"
#### 2-3-5) Discovery and cluster formation settings
#### 2-3-6) Setting the heap size
#### 2-3-7) JVM heap dump path
#### 2-3-8) GC logging
#### 2-3-9) Temp directory
#### 2-3-10) JVM fatal error logs
### 2-4. Important System Configuration
#### 2-4-1) Configuring system settings
#### 2-4-2) Disable swapping
#### 2-4-3) File Descriptors
#### 2-4-4) Virtual memory
#### 2-4-5) Number of threads
#### 2-4-6) DNS cache settings
#### 2-4-7) JNA temporary directory not mounted with "noexec"
### 2-5. Bootstrap Checks
#### 2-5-1) Heap size check
#### 2-5-2) File descriptor check
#### 2-5-3) Memory lock check
#### 2-5-4) Maximum number of threads check
#### 2-5-5) Max file size check
#### 2-5-6) Maximum size virtual memory check
#### 2-5-7) Maximum map count check
#### 2-5-8) Client JVM check
#### 2-5-9) Use serial collector check
#### 2-5-10) System call filter check
#### 2-5-11) OnError and OnOutOfMemoryError checks
#### 2-5-12) Early-access check
#### 2-5-13) G1GC check
#### 2-5-14) All permission check
#### 2-5-15) Discovery configuration check
### 2-6. Starting Elasticsearch
### 2-7. Stopping Elasticsearch
### 2-8. Adding nodes to your cluster
### 2-9. Set up X-Pack
### 2-10. Configuring monitoring
#### 2-10-1) Collecting monitoring data
#### 2-10-2) Collecting monitoring data with Metricbeat
#### 2-10-3) Configuring indices for monitoring
### 2-11. Configuring security
#### 2-11-1) Encrypting communications in Elasticsearch
#### 2-11-2) Encrypting communications in an Elasticsearch Docker Container
#### 2-11-3) Enabling Cipher Suites for Stronger Encryption
#### 2-11-4) Separating node-to-node and client traffic
#### 2-11-5) Configuring an Active Directory realm
#### 2-11-6) Configuring a file realm
#### 2-11-7) Configuring an LDAP realm
#### 2-11-8) Configuring a native realm
#### 2-11-9) Configuring a PKI realm
#### 2-11-10) Configuring a SAML realm
#### 2-11-11) Configuring a Kerberos realm
#### 2-11-12) FIPS 140-2
#### 2-11-13) Security files
### 2-12. Configuring X-Pack Java Clients
### 2-13. Bootstrap Checks for X-Pack

## [3] Upgrade Elasticsearch
### 3-1. Rolling upgrades
### 3-2. Full cluster restart upgrade
### 3-3. Reindex before upgrading
#### 3-3-1) Reindex in place
#### 3-3-2) Reindex from a remote cluster

## [4] API conventions
### 4-1. Multiple Indices
### 4-2. Date math support in index names
### 4-3. Common options
### 4-4. URL-based access control

## [5] Document APIs
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

## [6] Search APIs
### 6-1. Search
### 6-2. URI Search
### 6-3. Request Body Search
#### 6-3-1) Doc value Fields
#### 6-3-2) Explain
#### 6-3-3) Field Collapsing
#### 6-3-4) From / Size
#### 6-3-5) Highlighting
#### 6-3-6) Index Boost
#### 6-3-7) Inner hits
#### 6-3-8) min_score
#### 6-3-9) Named Queries
#### 6-3-10) Post filter
#### 6-3-11) Preference
#### 6-3-12) Query
#### 6-3-13) Rescoring
#### 6-3-14) Script Fields
#### 6-3-15) Scroll
#### 6-3-16) Search After
#### 6-3-17) Search Type
#### 6-3-18) Sequence Numbers and Primary Term
#### 6-3-19) Sort
#### 6-3-20) Source filtering
#### 6-3-21) Stored Fields
#### 6-3-22) Track total hits
#### 6-3-23) Version
### 6-4. Search Template
### 6-5. Multi Search Template
### 6-6. Search Shards API
### 6-7. Suggesters
#### 6-7-1) Term suggester
#### 6-7-2) Phrase Suggester
#### 6-7-3) Completion Suggester
#### 6-7-4) Context Suggester
#### 6-7-5) Returning the type of the suggester
### 6-8. Multi Search API
### 6-9. Count API
### 6-10. Validate API
### 6-11. Explain API
### 6-12. Profile API
#### 6-12-1) Profiling Queries
#### 6-12-2) Profiling Aggregations
#### 6-12-3) Profiling Considerations
### 6-13. Field Capabilities API
### 6-14. Ranking Evaluation API

## [7] Aggregations
### 7-1. Metrics Aggregations
#### 7-1-1) Avg Aggregation
#### 7-1-2) Weighted Avg Aggregation
#### 7-1-3) Cardinality Aggregation
#### 7-1-4) Extended Stats Aggregation
#### 7-1-5) Geo Bounds Aggregation
#### 7-1-6) Geo Centroid Aggregation
#### 7-1-7) Max Aggregation
#### 7-1-8) Min Aggregation
#### 7-1-9) Percentiles Aggregation
#### 7-1-10) Percentile Ranks Aggregation
#### 7-1-11) Scripted Metric Aggregation
#### 7-1-12) Stats Aggregation
#### 7-1-13) Sum Aggregation
#### 7-1-14) Top Hits Aggregation
#### 7-1-15) Value Count Aggregation
#### 7-1-16) Median Absolute Deviation Aggregation
### 7-2. Bucket Aggregations
#### 7-2-1) Adjacency Matrix Aggregation
#### 7-2-2) Auto-interval Date Histogram Aggregation
#### 7-2-3) Children Aggregation
#### 7-2-4) Composite Aggregation
#### 7-2-5) Date Histogram Aggregation
#### 7-2-6) Date Range Aggregation
#### 7-2-7) Diversified Sampler Aggregation
#### 7-2-8) Filter Aggregation
#### 7-2-9) Filters Aggregation
#### 7-2-10) Geo Distance Aggregation
#### 7-2-11) GeoHash grid Aggregation
#### 7-2-12) GeoTile Grid Aggregation
#### 7-2-13) Global Aggregation
#### 7-2-14) Histogram Aggregation
#### 7-2-15) IP Range Aggregation
#### 7-2-16) Missing Aggregation
#### 7-2-17) Nested Aggregation
#### 7-2-18) Parent Aggregation
#### 7-2-19) Range Aggregation
#### 7-2-20) Reverse nested Aggregation
#### 7-2-21) Sampler Aggregation
#### 7-2-22) Significant Terms Aggregation
#### 7-2-23) Significant Text Aggregation
#### 7-2-24) Terms Aggregation
### 7-3. Pipeline Aggregations
#### 7-3-1) Avg Bucket Aggregation
#### 7-3-2) Derivative Aggregation
#### 7-3-3) Max Bucket Aggregation
#### 7-3-4) Min Bucket Aggregation
#### 7-3-5) Sum Bucket Aggregation
#### 7-3-6) Stats Bucket Aggregation
#### 7-3-7) Extended Stats Bucket Aggregation
#### 7-3-8) Percentiles Bucket Aggregation
#### 7-3-9) Moving Average Aggregation
#### 7-3-10) Moving Function Aggregation
#### 7-3-11) Cumulative Sum Aggregation
#### 7-3-12) Bucket Script Aggregation
#### 7-3-13) Bucket Selector Aggregation
#### 7-3-14) Bucket Sort Aggregation
#### 7-3-15) Serial Differencing Aggregation
### 7-4. Matrix Aggregations
#### 7-4-1) Matrix Stats
### 7-5. Caching heavy aggregations
### 7-6. Returning only aggregation results
### 7-7. Aggregation Metadata
### 7-8. Returning the type of the aggregation

## [8] Indices APIs
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
### 8-16. Analyze
#### 8-16-1) Explain Analyze
### 8-17. Index Templates
### 8-18. Indices Stats
### 8-19. Indices Segments
### 8-20. Indices Recovery
### 8-21. Indices Shard Stores
### 8-22. Clear Cache
### 8-23. Flush
#### 8-23-1) Synced Flush
### 8-24. Refresh
### 8-25. Force Merge

## [9] cat APIs
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

## [10] Cluster APIs
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

## [11] Query DSL
### 11-1. Query and filter context
### 11-2. Match All Query
### 11-3. Full text queries
#### 11-3-1) Match Query
#### 11-3-2) Match Phrase Query
#### 11-3-3) Match Phrase Prefix Query
#### 11-3-4) Multi Match Query
#### 11-3-5) Common Terms Query
#### 11-3-6) Query String Query
#### 11-3-7) Simple Query String Query
#### 11-3-8) Intervals query
### 11-4. Term level queries
#### 11-4-1) Term Query
#### 11-4-2) Terms Query
#### 11-4-3) Terms Set Query
#### 11-4-4) Range Query
#### 11-4-5) Exists Query
#### 11-4-6) Prefix Query
#### 11-4-7) Wildcard Query
#### 11-4-8) Regexp Query
#### 11-4-9) Fuzzy Query
#### 11-4-10) Type Query
#### 11-4-11) Ids Query
### 11-5. Compound queries
#### 11-5-1) Constant Score Query
#### 11-5-2) Bool Query
#### 11-5-3) Dis Max Query
#### 11-5-4) Function Score Query
#### 11-5-5) Boosting Query
### 11-6. Joining queries
#### 11-6-1) Nested Query
#### 11-6-2) Has Child Query
#### 11-6-3) Has Parent Query
#### 11-6-4) Parent Id Query
### 11-7. Geo queries
#### 11-7-1) GeoShape Query
#### 11-7-2) Geo Bounding Box Query
#### 11-7-3) Geo Distance Query
#### 11-7-4) Geo Polygon Query
### 11-8. Specialized queries
#### 11-8-1) More Like This Query
#### 11-8-2) Script Query
#### 11-8-3) Script Score Query
#### 11-8-4) Percolate Query
#### 11-8-5) Rank Feature Query
#### 11-8-6) Wrapper Query
### 11-9. Span queries
#### 11-9-1) Span Term Query
#### 11-9-2) Span Multi Term Query
#### 11-9-3) Span First Query
#### 11-9-4) Span Near Query
#### 11-9-5) Span Or Query
#### 11-9-6) Span Not Query
#### 11-9-7) Span Containing Query
#### 11-9-8) Span Within Query
#### 11-9-9) Span Field Masking Query
### 11-10. Minimum Should Match
### 11-11. Multi Term Query Rewrite

## [12] Mapping
### 12-1. Removal of mapping types
### 12-2. Field datatypes
#### 12-2-1) Alias datatype
#### 12-2-2) Array datatype
#### 12-2-3) Binary datatype
#### 12-2-4) Range datatypes
#### 12-2-5) Boolean datatype
#### 12-2-6) Date datatype
#### 12-2-7) date_nanos datatype
#### 12-2-8) Geo-point datatype
#### 12-2-9) Geo-Shape datatype
#### 12-2-10) IP datatype
#### 12-2-11) Keyword datatype
#### 12-2-12) Nested datatype
#### 12-2-13) Numeric datatypes
#### 12-2-14) Object datatype
#### 12-2-15) Text datatype
#### 12-2-16) Token count datatype
#### 12-2-17) Percolator type
#### 12-2-18) "join" datatype
#### 12-2-19) Rank feature datatype
#### 12-2-20) Rank features datatype
#### 12-2-21) Dense vector datatype
#### 12-2-22) Sparse vector datatype
### 12-3. Meta-Fields
#### 12-3-1) "_field_names" field
#### 12-3-2) "_ignored" field
#### 12-3-3) "_id" field
#### 12-3-4) "_index" field
#### 12-3-5) "_meta" field
#### 12-3-6) "_routing" field
#### 12-3-7) "_source" field
#### 12-3-8) "_type" field
### 12-4. Mapping parameters
#### 12-4-1) "analyzer"
#### 12-4-2) "normalizer"
#### 12-4-3) "boost"
#### 12-4-4) "coerce"
#### 12-4-5) "copy_to"
#### 12-4-6) "doc_values"
#### 12-4-7) "dynamic"
#### 12-4-8) "enabled"
#### 12-4-9) "eager_global_ordinals"
#### 12-4-10) "fielddata"
#### 12-4-11) "format"
#### 12-4-12) "ignore_above"
#### 12-4-13) "ignore_malformed"
#### 12-4-14) "index"
#### 12-4-15) "index_options"
#### 12-4-16) "index_phrases"
#### 12-4-17) "index_prefixes"
#### 12-4-18) "fields"
#### 12-4-19) "norms"
#### 12-4-20) "null_value"
#### 12-4-21) "position_increment_gap"
#### 12-4-22) "properties"
#### 12-4-23) "search_analyzer"
#### 12-4-24) "similarity"
#### 12-4-25) "store"
#### 12-4-26) "term_vector"
### 12-5. Dynamic Mapping
#### 12-5-1) Dynamic field mapping
#### 12-5-2) Dynamic templates

## [13] Analysis
### 13-1. Anatomy of an analyzer
### 13-2. Testing analyzers
### 13-3. Analyzers
#### 13-3-1) Configuring built-in analyzers
#### 13-3-2) Standard Analyzer
#### 13-3-3) Simple Analyzer
#### 13-3-4) Whitespace Analyzer
#### 13-3-5) Stop Analyzer
#### 13-3-6) Keyword Analyzer
#### 13-3-7) Pattern Analyzer
#### 13-3-8) Language Analyzers
#### 13-3-9) Fingerprint Analyzer
#### 13-3-10) Custom Analyzer
### 13-4. Normalizers
### 13-5. Tokenizers
#### 13-5-1) Standard Tokenizer
#### 13-5-2) Letter Tokenizer
#### 13-5-3) Lowercase Tokenizer
#### 13-5-4) Whitespace Tokenizer
#### 13-5-5) UAX URL Email Tokenizer
#### 13-5-6) Classic Tokenizer
#### 13-5-7) Thai Tokenizer
#### 13-5-8) NGram Tokenizer
#### 13-5-9) Edge NGram Tokenizer
#### 13-5-10) Keyword Tokenizer
#### 13-5-11) Pattern Tokenizer
#### 13-5-12) Char Group Tokenizer
#### 13-5-13) Simple Pattern Tokenizer
#### 13-5-14) Simple Pattern Split Tokenizer
#### 13-5-15) Path Hierarchy Tokenizer
### 13-6. Token Filters
#### 13-6-1) ASCII Folding Token Filter
#### 13-6-2) Flatten Graph Token Filter
#### 13-6-3) Length Token Filter
#### 13-6-4) Lowercase Token Filter
#### 13-6-5) Uppercase Token Filter
#### 13-6-6) NGram Token Filter
#### 13-6-7) Edge NGram Token Filter
#### 13-6-8) Porter Stem Token Filter
#### 13-6-9) Shingle Token Filter
#### 13-6-10) Stop Token Filter
#### 13-6-11) Word Delimiter Token Filter
#### 13-6-12) Word Delimiter Graph Token Filter
#### 13-6-13) Multiplexer Token Filter
#### 13-6-14) Conditional Token Filter
#### 13-6-15) Predicate Token Filter Script
#### 13-6-16) Stemmer Token Filter
#### 13-6-17) Stemmer Override Token Filter
#### 13-6-18) Keyword Marker Token Filter
#### 13-6-19) Keyword Repeat Token Filter
#### 13-6-20) KStem Token Filter
#### 13-6-21) Snowball Token Filter
#### 13-6-22) Phonetic Token Filter
#### 13-6-23) Synonym Token Filter
#### 13-6-24) Parsing synonym files
#### 13-6-25) Synonym Graph Token Filter
#### 13-6-26) Compound Word Token Filters
#### 13-6-27) Reverse Token Filter
#### 13-6-28) Elision Token Filter
#### 13-6-29) Truncate Token Filter
#### 13-6-30) Unique Token Filter
#### 13-6-31) Pattern Capture Token Filter
#### 13-6-32) Pattern Replace Token Filter
#### 13-6-33) Trim Token Filter
#### 13-6-34) Limit Token Count Token Filter
#### 13-6-35) Hunspell Token Filter
#### 13-6-36) Common Grams Token Filter
#### 13-6-37) Normalization Token Filter
#### 13-6-38) CJK Width Token Filter
#### 13-6-39) CJK Bigram Token Filter
#### 13-6-40) Delimited Payload Token Filter
#### 13-6-41) Keep Words Token Filter
#### 13-6-42) Keep Types Token Filter
#### 13-6-43) Exclude mode settings example
#### 13-6-44) Classic Token Filter
#### 13-6-45) Apostrophe Token Filter
#### 13-6-46) Decimal Digit Token Filter
#### 13-6-47) Fingerprint Token Filter
#### 13-6-48) Minhash Token Filter
#### 13-6-49) Remove Duplicates Token Filter
### 13-7. Character Filters
#### 13-7-1) HTML Strip Char Filter
#### 13-7-2) Mapping Char Filter
#### 13-7-3) Pattern Replace Char Filter

## [14] Modules
### 14-1. Discovery and cluster formation
#### 14-1-1) Discovery
#### 14-1-2) Quorum-based decision making
#### 14-1-3) Voting configurations
#### 14-1-4) Bootstrapping a cluster
#### 14-1-5) Adding and removing nodes
#### 14-1-6) Publishing the cluster state
#### 14-1-7) Cluster fault detection
#### 14-1-8) Discovery and cluster formation settings
### 14-2. Shard allocation and cluster-level routing
#### 14-2-1) Cluster level shard allocation
#### 14-2-2) Disk-based shard allocation
#### 14-2-3) Shard allocation awareness
#### 14-2-4) Cluster-level shard allocation filtering
#### 14-2-5) Miscellaneous cluster settings
### 14-3. Local Gateway
#### 14-3-1) Dangling indices
### 14-4. HTTP
### 14-5. Indices
#### 14-5-1) Circuit Breaker
#### 14-5-2) Fielddata
#### 14-5-3) Node Query Cache
#### 14-5-4) Indexing Buffer
#### 14-5-5) Shard request cache
#### 14-5-6) Indices Recovery
#### 14-5-7) Search Settings
### 14-6. Network Settings
### 14-7. Node
### 14-8. Plugins
### 14-9. Scripting
#### 14-9-1) How to use scripts
#### 14-9-2) Accessing document fields and special variables
#### 14-9-3) Scripting and security
#### 14-9-4) Painless Scripting Language
#### 14-9-5) Lucene Expressions Language
#### 14-9-6) Advanced scripts using script engines
### 14-10. Snapshot and Restore
### 14-11. Thread Pool
### 14-12. Transport
### 14-13. Remote clusters
### 14-14. Cross-cluster search

## [15] Index modules
### 15-1. Analysis
### 15-2. Index Shard Allocation
#### 15-2-1) Index-level shard allocation filtering
#### 15-2-2) Delaying allocation when a node leaves
#### 15-2-3) Index recovery prioritization
#### 15-2-4) Total shards per node
### 15-3. Mapper
### 15-4. Merge
### 15-5. Similarity module
### 15-6. Slow Log
### 15-7. Store
#### 15-7-1) Pre-loading data into the file system cache
### 15-8. Translog
### 15-9. Index Sorting
#### 15-9-1) Use index sorting to speed up conjunctions

## [16] Ingest node
### 16-1. Pipeline Definition
### 16-2. Ingest APIs
#### 16-2-1) Put Pipeline API
#### 16-2-2) Get Pipeline API
#### 16-2-3) Delete Pipeline API
#### 16-2-4) Simulate Pipeline API
### 16-3. Accessing Data in Pipelines
### 16-4. Conditional Execution in Pipelines
#### 16-4-1) Handling Nested Fields in Conditionals
#### 16-4-2) Complex Conditionals
#### 16-4-3) Conditionals with the Pipeline Processor
#### 16-4-4) Conditionals with the Regular Expressions
### 16-5. Handling Failures in Pipelines
### 16-6. Processors
#### 16-6-1) Append Processor
#### 16-6-2) Bytes Processor
#### 16-6-3) Convert Processor
#### 16-6-4) Date Processor
#### 16-6-5) Date Index Name Processor
#### 16-6-6) Dissect Processor
#### 16-6-7) Dot Expander Processor
#### 16-6-8) Drop Processor
#### 16-6-9) Fail Processor
#### 16-6-10) Foreach Processor
#### 16-6-11) GeoIP Processor
#### 16-6-12) Grok Processor
#### 16-6-13) Gsub Processor
#### 16-6-14) Join Processor
#### 16-6-15) JSON Processor
#### 16-6-16) KV Processor
#### 16-6-17) Pipeline Processor
#### 16-6-18) Remove Processor
#### 16-6-19) Rename Processor
#### 16-6-20) Script Processor
#### 16-6-21) Set Processor
#### 16-6-22) Set Security User Processor
#### 16-6-23) Split Processor
#### 16-6-24) Sort Processor
#### 16-6-25) Trim Processor
#### 16-6-26) Uppercase Processor
#### 16-6-27) URL Decode Processor
#### 16-6-28) User Agent processor

## [17] Managing the index lifecycle
### 17-1. Getting started with index lifecycle management
### 17-2. Policy phases and actions
#### 17-2-1) Timing
#### 17-2-2) Phase Execution
#### 17-2-3) Actions
#### 17-2-4) Full Policy
### 17-3. Set up index lifecycle management policy
#### 17-3-1) Applying a policy to an index template
#### 17-3-2) Apply a policy to a create index request
### 17-4. Using policies to manage index rollover
#### 17-4-1) Skipping Rollover
### 17-5. Update policy
#### 17-5-1) Updates to policies not managing indices
#### 17-5-2) Updates to executing policies
#### 17-5-3) Switching policies for an index
### 17-6. Index lifecycle error handling
### 17-7. Restoring snapshots of managed indices
### 17-8. Start and stop index lifecycle management

## [18] SQL access
### 18-1. Overview
### 18-2. Getting Started with SQL
### 18-3. Conventions and Terminology
#### 18-3-1) Mapping concepts across SQL and Elasticsearch
### 18-4. Security
### 18-5. SQL REST API
### 18-6. SQL Translate API
### 18-7. SQL CLI
### 18-8. SQL JDBC
#### 18-8-1) API usage
### 18-9. SQL ODBC
#### 18-9-1) Driver installation
#### 18-9-2) Configuration
### 18-10. SQL Client Applications
#### 18-10-1) DBeaver
#### 18-10-2) DbVisualizer
#### 18-10-3) Microsoft Excel
#### 18-10-4) Microsoft Power BI Desktop
#### 18-10-5) Microsoft PowerShell
#### 18-10-6) MicroStrategy Desktop
#### 18-10-7) Qlik Sense Desktop
#### 18-10-8) SQuirreL SQL
#### 18-10-9) SQL Workbench/J
#### 18-10-10) Tableau Desktop
### 18-11. SQL Language
### 18-12. Lexical Structure
### 18-13. SQL Commands
#### 18-13-1) DESCRIBE TABLE
#### 18-13-2) SELECT
#### 18-13-3) SHOW COLUMNS
#### 18-13-4) SHOW FUNCTIONS
#### 18-13-5) SHOW TABLES
### 18-14. Data Types
### 18-15. Index patterns
### 18-16. Functions and Operators
#### 18-16-1) Comparison Operators
#### 18-16-2) Logical Operators
#### 18-16-3) Math Operators
#### 18-16-4) LIKE and RLIKE Operators
#### 18-16-5) Aggregate Functions
#### 18-16-6) Grouping Functions
#### 18-16-7) Date/Time and Interval Functions and Operators
#### 18-16-8) Full-Text Search Functions
#### 18-16-9) Mathematical Functions
#### 18-16-10) String Functions
#### 18-16-11) Type Conversion Functions
#### 18-16-12) Conditional Functions
#### 18-16-13) System Functions
### 18-17. Reserved keywords
### 18-18. SQL Limitations

## [19] Monitoring Elasticsearch
### 19-1. Collectors
### 19-2. Exporters
#### 19-2-1. Local Exporters
#### 19-2-2. HTTP Exporters
### 19-3. Pausing Data Collection

## [20] Rolling up historical data
### 20-1. Overview
### 20-2. API Quick Reference
### 20-3. Getting Started
### 20-4. Understanding Groups
#### 20-4-1) Grouping Limitations with heterogeneous indices
#### 20-4-2) Doc counts and overlapping jobs
### 20-5. Rollup Aggregation Limitations
### 20-6. Rollup Search Limitations

## [21] Frozen indices
### 21-1. Best practices
### 21-2. Searching a frozen index
### 21-3. Monitoring frozen indices

## [22] X-Pack APIs
### 22-1. Info API
### 22-2. Cross-cluster replication APIs
#### 22-2-1) Get CCR stats
#### 22-2-2) Create follower
#### 22-2-3) Pause follower
#### 22-2-4) Resume follower
#### 22-2-5) Unfollow
#### 22-2-6) Forget Follower
#### 22-2-7) Get follower stats
#### 22-2-8) Get follower info
#### 22-2-9) Create auto-follow pattern
#### 22-2-10) Delete auto-follow pattern
#### 22-2-11) Get auto-follow pattern
### 22-3. Explore API
### 22-4. Freeze index
### 22-5. Index lifecycle management API
#### 22-5-1) Create policy
#### 22-5-2) Get policy
#### 22-5-3) Delete policy
#### 22-5-4) Move to step
#### 22-5-5) Remove policy
#### 22-5-6) Retry policy
#### 22-5-7) Get index lifecycle management status
#### 22-5-8) Explain lifecycle
#### 22-5-9) Start index lifecycle management
#### 22-5-10) Stop index lifecycle management
### 22-6. Licensing APIs
#### 22-6-1) Delete license
#### 22-6-2) Get license
#### 22-6-3) Get trial status
#### 22-6-4) Start trial
#### 22-6-5) Get basic status
#### 22-6-6) Start basic
#### 22-6-7) Update license
### 22-7. Migration APIs
#### 22-7-1) Deprecation info
### 22-8. Machine learning APIs
#### 22-8-1) Add events to calendar
#### 22-8-2) Add jobs to calendar
#### 22-8-3) Close jobs
#### 22-8-4) Create calendar
#### 22-8-5) Create datafeeds
#### 22-8-6) Create filter
#### 22-8-7) Create jobs
#### 22-8-8) Delete calendar
#### 22-8-9) Delete datafeeds
#### 22-8-10) Delete events from calendar
#### 22-8-11) Delete filter
#### 22-8-12) Delete forecast
#### 22-8-13) Delete jobs
#### 22-8-14) Delete jobs from calendar
#### 22-8-15) Delete model snapshots
#### 22-8-16) Delete expired data
#### 22-8-17) Find file structure
#### 22-8-18) Flush jobs
#### 22-8-19) Forecast jobs
#### 22-8-20) Get calendars
#### 22-8-21) Get buckets
#### 22-8-22) Get overall buckets
#### 22-8-23) Get categories
#### 22-8-24) Get datafeeds
#### 22-8-25) Get datafeed statistics
#### 22-8-26) Get influencers
#### 22-8-27) Get jobs
#### 22-8-28) Get job statistics
#### 22-8-29) Get machine learning info
#### 22-8-30) Get model snapshots
#### 22-8-31) Get scheduled events
#### 22-8-32) Get filters
#### 22-8-33) Get records
#### 22-8-34) Open jobs
#### 22-8-35) Post data to jobs
#### 22-8-36) Preview datafeeds
#### 22-8-37) Revert model snapshots
#### 22-8-38) Set upgrade mode
#### 22-8-39) Start datafeeds
#### 22-8-40) Stop datafeeds
#### 22-8-41) Update datafeeds
#### 22-8-42) Update filter
#### 22-8-43) Update jobs
#### 22-8-44) Update model snapshots
### 22-9. Rollup APIs
#### 22-9-1) Delete job
#### 22-9-2) Get job
#### 22-9-3) Create job
#### 22-9-4) Start job
#### 22-9-5) Stop job
#### 22-9-6) Get rollup caps
#### 22-9-7) Get rollup index caps
#### 22-9-8) Rollup search
#### 22-9-9) Rollup job configuration
### 22-10. Security APIs
#### 22-10-1) Authenticate
#### 22-10-2) Change passwords
#### 22-10-3) Clear cache
#### 22-10-4) Clear roles cache
#### 22-10-5) Create API keys
#### 22-10-6) Create or update application privileges
#### 22-10-7) Create or update role mappings
#### 22-10-8) Create or update roles
#### 22-10-9) Create or update users
#### 22-10-10) Delete application privileges
#### 22-10-11) Delete role mappings
#### 22-10-12) Delete roles
#### 22-10-13) Delete users
#### 22-10-14) Disable users
#### 22-10-15) Enable users
#### 22-10-16) Get API key information
#### 22-10-17) Get application privileges
#### 22-10-18) Get role mappings
#### 22-10-19) Get roles
#### 22-10-20) Get token
#### 22-10-21) Get users
#### 22-10-22) Has privileges
#### 22-10-23) Invalidate API key
#### 22-10-24) Invalidate token
#### 22-10-25) SSL certificate
### 22-11. Unfreeze index
### 22-12. Watcher APIs
#### 22-12-1) Put watch
#### 22-12-2) Get watch
#### 22-12-3) Delete watch
#### 22-12-4) Execute watch
#### 22-12-5) Ack watch
#### 22-12-6) Activate watch
#### 22-12-7) Deactivate watch
#### 22-12-8) Stats
#### 22-12-9) Stop
#### 22-12-10) Start
### 22-13. Definitions
#### 22-13-1) Calendar resources
#### 22-13-2) Datafeed resources
#### 22-13-3) Filter resources
#### 22-13-4) Job resources
#### 22-13-5) Job statistics
#### 22-13-6) Model snapshot resources
#### 22-13-7) Role mapping resources
#### 22-13-8) Results resources
#### 22-13-9) Scheduled event resources

## [23] Command line tools
### 23-1. elasticsearch-certgen
### 23-2. elasticsearch-certutil
### 23-3. elasticsearch-migrate
### 23-4. elasticsearch-node
### 23-5. elasticsearch-saml-metadata
### 23-6. elasticsearch-setup-passwords
### 23-7. elasticsearch-shard
### 23-8. elasticsearch-syskeygen
### 23-9. elasticsearch-users

## [24] How To
### 24-1. General recommendations
### 24-2. Recipes
#### 24-2-1) Mixing exact search with stemming
#### 24-2-2) Getting consistent scoring
#### 24-2-3) Incorporating static relevance signals into the score
### 24-3. Tune for indexing speed
### 24-4. Tune for search speed
#### 24-4-1) Tune your queries with the Profile API
#### 24-4-2) Faster phrase queries with "index_phrases"
#### 24-4-3) Faster prefix queries with "index_prefixes"
### 24-5. Tune for disk usage

## [25] Testing
### 25-1. Java Testing Framework
#### 25-1-1) Why randomized testing?
#### 25-1-2) Using the Elasticsearch test classes
#### 25-1-3) Unit tests
#### 25-1-4) Integration tests
#### 25-1-5) Randomized testing
#### 25-1-6) Assertions