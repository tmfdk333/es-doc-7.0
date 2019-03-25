# [Elasticsearch Reference: 6.6](https://www.elastic.co/guide/en/elasticsearch/reference/6.6/getting-started.html)

## Getting Started
- Basic Concepts
- Installation
- Exploring Your Cluster
    - Cluster Health
    - List All Indices
    - Create an Index
    - Index and Query a Document
    - Delete an Index
- Modifying Your Data
    - Updating Documents
    - Deleting Documents
    - Batch Processing
- Exploring Your Data
    - The Search API
    - Introducing the Query Language
    - Executing Searches
    - Executing Filters
    - Executing Aggregations
- Conclusion



## [[1] Set up Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/6.6/setup.html)
* Supported platforms
* Java (JVM) Version

### [1-1. Installing Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/6.6/install-elasticsearch.html)
* Hosted Elasticsearch
* Installing Elasticsearch Yourself
* Configuration Management Tools  

- **[Install Elasticsearch with .zip or .tar.gz](https://www.elastic.co/guide/en/elasticsearch/reference/6.6/zip-targz.html#setup-installation-daemon)**
    - Download and install the .zip package
    - Download and install the .tar.gz package
    - Enable automatic creation of X-Pack indices
    - Running Elasticsearch from the command line
    - Checking that Elasticsearch is running
    - Running as a daemon
    - Configuring Elasticsearch on the command line
    - Directory layout of .zip and .tar.gz archives
    - Next steps
- **[Install Elasticsearch with .zip on Windows](https://www.elastic.co/guide/en/elasticsearch/reference/6.6/zip-windows.html)**
- **[Install Elasticsearch with Debian Package](https://www.elastic.co/guide/en/elasticsearch/reference/6.6/deb.html)**
- **[Install Elasticsearch with RPM](https://www.elastic.co/guide/en/elasticsearch/reference/6.6/rpm.html)**
- **[Install Elasticsearch with Windows MSI Installer](https://www.elastic.co/guide/en/elasticsearch/reference/6.6/windows.html)**
- **[Install Elasticsearch with Docker](https://www.elastic.co/guide/en/elasticsearch/reference/6.6/docker.html)**

### [1-2. Configuring Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/6.6/settings.html)
* Config files location
* Config file format
* Environment variable substitution
* Prompting for settings **`!Deprecated!`**

- **[Setting JVM options](https://www.elastic.co/guide/en/elasticsearch/reference/6.6/jvm-options.html)**
- **[Secure settings](https://www.elastic.co/guide/en/elasticsearch/reference/6.6/secure-settings.html)**
    - Creating the keystore
    - Listing settings in the keystore
    - Adding string settings
    - Removing settings
    - Reloadable secure settings
- **[Logging configuration](https://www.elastic.co/guide/en/elasticsearch/reference/6.6/logging.html)**
    - Configuring logging levels
    - Deprecation logging

### [1-3. Important Elasticsearch configuration]
- `path.data` and `path.logs`
- `cluster.name`
- `node.name`
- `network.host`
- Discovery settings
- Setting the heap size
- JVM heap dump path
- GC logging
- Temp directory
- JVM fatal error logs

### [1-4. Important System Configuration]
- Configuring system settings
- Disable swapping
- File Descriptors
- Virtual memory
- Number of threads
- DNS cache settings
- JNA temporary directory not mounted with noexec

### [1-5. Bootstrap Checks]
- Heap size check
- File descriptor check
- Memory lock check
- Maximum number of threads check
- Max file size check
- Maximum size virtual memory check
- Maximum map count check
- Client JVM check
- Use serial collector check
- System call filter check
- OnError and OnOutOfMemoryError checks
- Early-access check
- G1GC check
- All permission check

### [1-6. Starting Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/6.6/starting-elasticsearch.html)
- Archive packages (.tar.gz)
- Archive packages (.zip)
- Debian packages
- Docker images
- MSI packages
- RPM packages

### [1-7. Stopping Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/6.6/stopping-elasticsearch.html)
- Stopping on Fatal Errors

### [1-8. Adding nodes to your cluster]

### [1-9. Installing X-Pack]

### [1-10. Set up X-Pack]

### [1-11. Configuring monitoring]
- Collecting monitoring data
- Collecting monitoring data with Metricbeat
- Configuring indices for monitoring
- Configuring a Tribe Node to Work with Monitoring
- Monitoring settings

### [1-12. Configuring security]
- Encrypting communications in Elasticsearch
- Encrypting communications in an Elasticsearch Docker Container
- Enabling Cipher Suites for Stronger Encryption
- Separating node-to-node and client traffic
- Configuring an Active Directory realm
- Configuring a file realm
- Configuring an LDAP realm
- Configuring a native realm
- Configuring a PKI realm
- Configuring a SAML realm
- Configuring a Kerberos realm
- FIPS 140-2
- Security settings
- Security files
- Auditing Settings

### [1-13. Configuring X-Pack Java Clients]

### [1-14. X-Pack Settings]
- License Settings
- Machine learning settings
- Watcher Settings
- SQL Access Settings

### [1-15. Bootstrap Checks for X-Pack]

## Upgrade Elasticsearch
- Rolling upgrades
- Full cluster restart upgrade
- Reindex before upgrading
    - Reindex in place
    - Reindex from a remote cluster

## API Conventions
- Multiple Indices
- Date math support in index names
- Common options
- URL-based access control

## Document APIs
- Reading and Writing documents
- Index API
- Get API
- Delete API
- Delete By Query API
- Update API
- Update By Query API
- Multi Get API
- Bulk API
- Reindex API
- Term Vectors
- Multi termvectors API
- `?refresh`
- Optimistic concurrency control

## Search APIs
- Search
- URI Search
- Request Body Search
    - Query
    - From / Size
    - Sort
    - Source filtering
    - Fields
    - Script Fields
    - Doc value Fields
    - Post filter
    - Highlighting
    - Rescoring
    - Search Type
    - Scroll
    - Preference
    - Explain
    - Version
    - Index Boost
    - min_score
    - Named Queries
    - Inner hits
    - Field Collapsing
    - Search After
- Search Template
- Multi Search Template
- Search Shards API
- Suggesters
    - Term suggester
    - Phrase Suggester
    - Completion Suggester
    - Context Suggester
    - Returning the type of the suggester
- Multi Search API
- Count API
- Validate API
- Explain API
- Profile API
    - Profiling Queries
    - Profiling Aggregations
    - Profiling Considerations
- Field Capabilities API
- Ranking Evaluation API

## Aggregations
- Metrics Aggregations
    - Avg Aggregation
    - Weighted Avg Aggregation
    - Cardinality Aggregation
    - Extended Stats Aggregation
    - Geo Bounds Aggregation
    - Geo Centroid Aggregation
    - Max Aggregation
    - Min Aggregation
    - Percentiles Aggregation
    - Percentile Ranks Aggregation
    - Scripted Metric Aggregation
    - Stats Aggregation
    - Sum Aggregation
    - Top Hits Aggregation
    - Value Count Aggregation
    - Median Absolute Deviation Aggregation
- Bucket Aggregations
    - Adjacency Matrix Aggregation
    - Auto-interval Date Histogram Aggregation
    - Intervals
    - Children Aggregation
    - Composite Aggregation
    - Date Histogram Aggregation
    - Date Range Aggregation
    - Diversified Sampler Aggregation
    - Filter Aggregation
    - Filters Aggregation
    - Geo Distance Aggregation
    - GeoHash grid Aggregation
    - Global Aggregation
    - Histogram Aggregation
    - IP Range Aggregation
    - Missing Aggregation
    - Nested Aggregation
    - Parent Aggregation
    - Range Aggregation
    - Reverse nested Aggregation
    - Sampler Aggregation
    - Significant Terms Aggregation
    - Significant Text Aggregation
    - Terms Aggregation
- Pipeline Aggregations
    - Avg Bucket Aggregation
    - Derivative Aggregation
    - Max Bucket Aggregation
    - Min Bucket Aggregation
    - Sum Bucket Aggregation
    - Stats Bucket Aggregation
    - Extended Stats Bucket Aggregation
    - Percentiles Bucket Aggregation
    - Moving Average Aggregation
    - Moving Function Aggregation
    - Cumulative Sum Aggregation
    - Bucket Script Aggregation
    - Bucket Selector Aggregation
    - Bucket Sort Aggregation
    - Serial Differencing Aggregation
- Matrix Aggregations
    - Matrix Stats
- Caching heavy aggregations
- Returning only aggregation results
- Aggregation Metadata
- Returning the type of the aggregation

## Indices APIs
- Create Index
- Delete Index
- Get Index
- Indices Exists
- Open / Close Index API
- Shrink Index
- Split Index
- Rollover Index
- Put Mapping
- Get Mapping
- Get Field Mapping
- Types Exists
- Index Aliases
- Update Indices Settings
- Get Settings
- Analyze
    - Explain Analyze
- Index Templates
- Indices Stats
- Indices Segments
- Indices Recovery
- Indices Shard Stores
- Clear Cache
- Flush
    - Synced Flush
- Refresh
- Force Merge

## cat APIs
- cat aliases
- cat allocation
- cat count
- cat fielddata
- cat health
- cat indices
- cat master
- cat nodeattrs
- cat nodes
- cat pending tasks
- cat plugins
- cat recovery
- cat repositories
- cat thread pool
- cat shards
- cat segments
- cat snapshots
- cat templates

## Cluster APIs
- Cluster Health
- Cluster State
- Cluster Stats
- Pending cluster tasks
- Cluster Reroute
- Cluster Update Settings
- Cluster Get Settings
- Nodes Stats
- Nodes Info
- Nodes Feature Usage
- Remote Cluster Info
- Task Management API
- Nodes hot_threads
- Cluster Allocation Explain API

## Query DSL
- Query and filter context
- Match All Query
- Full text queries
    - Match Query
    - Match Phrase Query
    - Match Phrase Prefix Query
    - Multi Match Query
    - Common Terms Query
    - Query String Query
    - Simple Query String Query
- Term level queries
    - Term Query
    - Terms Query
    - Terms Set Query
    - Range Query
    - Exists Query
    - Prefix Query
    - Wildcard Query
    - Regexp Query
    - Fuzzy Query
    - Type Query
    - Ids Query
- Compound queries
    - Constant Score Query
    - Bool Query
    - Dis Max Query
    - Function Score Query
    - Boosting Query
- Joining queries
    - Nested Query
    - Has Child Query
    - Has Parent Query
    - Parent Id Query
- Geo queries
    - GeoShape Query
    - Geo Bounding Box Query
    - Geo Distance Query
    - Geo Polygon Query
- Specialized queries
    - More Like This Query
    - Script Query
    - Percolate Query
    - Wrapper Query
- Span queries
    - Span Term Query
    - Span Multi Term Query
    - Span First Query
    - Span Near Query
    - Span Or Query
    - Span Not Query
    - Span Containing Query
    - Span Within Query
    - Span Field Masking Query
- Minimum Should Match
- Multi Term Query Rewrite

## Mapping
- Removal of mapping types
- Field datatypes
    - Alias datatype
    - Array datatype
    - Binary datatype
    - Range datatypes
    - Boolean datatype
    - Date datatype
    - Geo-point datatype
    - Geo-Shape datatype
    - IP datatype
    - Keyword datatype
    - Nested datatype
    - Numeric datatypes
    - Object datatype
    - Text datatype
    - Token count datatype
    - Percolator type
    - join datatype
- Meta-Fields
    - _all field
    - _field_names field
    - _ignored field
    - _id field
    - _index field
    - _meta field
    - _routing field
    - _source field
    - _type field
    - _uid field
- Mapping parameters
    - analyzer
    - normalizer
    - boost
    - coerce
    - copy_to
    - doc_values
    - dynamic
    - enabled
    - eager_global_ordinals
    - fielddata
    - format
    - ignore_above
    - ignore_malformed
    - index
    - index_options
    - index_phrases
    - index_prefixes
    - fields
    - norms
    - null_value
    - position_increment_gap
    - properties
    - search_analyzer
    - similarity
    - store
    - term_vector
- Dynamic Mapping
    - Dynamic field mapping
    - Dynamic templates
    - _default_ mapping

## Analysis
- Anatomy of an analyzer
- Testing analyzers
- Analyzers
    - Configuring built-in analyzers
    - Standard Analyzer
    - Simple Analyzer
    - Whitespace Analyzer
    - Stop Analyzer
    - Keyword Analyzer
    - Pattern Analyzer
    - Language Analyzers
    - Fingerprint Analyzer
    - Custom Analyzer
- Normalizers
- Tokenizers
    - Standard Tokenizer
    - Letter Tokenizer
    - Lowercase Tokenizer
    - Whitespace Tokenizer
    - UAX URL Email Tokenizer
    - Classic Tokenizer
    - Thai Tokenizer
    - NGram Tokenizer
    - Edge NGram Tokenizer
    - Keyword Tokenizer
    - Pattern Tokenizer
    - Char Group Tokenizer
    - Simple Pattern Tokenizer
    - Simple Pattern Split Tokenizer
    - Path Hierarchy Tokenizer
- Token Filters
    - Standard Token Filter
    - ASCII Folding Token Filter
    - Flatten Graph Token Filter
    - Length Token Filter
    - Lowercase Token Filter
    - Uppercase Token Filter
    - NGram Token Filter
    - Edge NGram Token Filter
    - Porter Stem Token Filter
    - Shingle Token Filter
    - Stop Token Filter
    - Word Delimiter Token Filter
    - Word Delimiter Graph Token Filter
    - Multiplexer Token Filter
    - Conditional Token Filter
    - Predicate Token Filter Script
    - Stemmer Token Filter
    - Stemmer Override Token Filter
    - Keyword Marker Token Filter
    - Keyword Repeat Token Filter
    - KStem Token Filter
    - Snowball Token Filter
    - Phonetic Token Filter
    - Synonym Token Filter
    - Parsing synonym files
    - Synonym Graph Token Filter
    - Parsing synonym files
    - Compound Word Token Filters
    - Reverse Token Filter
    - Elision Token Filter
    - Truncate Token Filter
    - Unique Token Filter
    - Pattern Capture Token Filter
    - Pattern Replace Token Filter
    - Trim Token Filter
    - Limit Token Count Token Filter
    - Hunspell Token Filter
    - Common Grams Token Filter
    - Normalization Token Filter
    - CJK Width Token Filter
    - CJK Bigram Token Filter
    - Delimited Payload Token Filter
    - Keep Words Token Filter
    - Keep Types Token Filter
    - Exclude mode settings example
    - Classic Token Filter
    - Apostrophe Token Filter
    - Decimal Digit Token Filter
    - Fingerprint Token Filter
    - Minhash Token Filter
    - Remove Duplicates Token Filter
- Character Filters
    - HTML Strip Char Filter
    - Mapping Char Filter
    - Pattern Replace Char Filter

## Modules
- Cluster
    - Cluster Level Shard Allocation
    - Disk-based Shard Allocation
    - Shard Allocation Awareness
    - Shard Allocation Filtering
    - Miscellaneous cluster settings
- Discovery
    - Azure Classic Discovery
    - EC2 Discovery
    - Google Compute Engine Discovery
    - Zen Discovery
- Local Gateway
- HTTP
- Indices
    - Circuit Breaker
    - Fielddata
    - Node Query Cache
    - Indexing Buffer
    - Shard request cache
    - Indices Recovery
    - Search Settings
- Network Settings
- Node
- Plugins
- Scripting
    - How to use scripts
    - Accessing document fields and special variables
    - Scripting and security
    - Painless Scripting Language
    - Lucene Expressions Language
    - Advanced scripts using script engines
- Snapshot And Restore
- Thread Pool
- Transport
- Tribe node
- Remote clusters
- Cross-cluster search

## Index Modules
- Analysis
- Index Shard Allocation
    - Shard Allocation Filtering
    - Delaying allocation when a node leaves
    - Index recovery prioritization
    - Total Shards Per Node
- Mapper
- Merge
- Similarity module
- Slow Log
- Store
    - Pre-loading data into the file system cache
- Translog
- Index Sorting
    - Use index sorting to speed up conjunctions

## Ingest Node
- Pipeline Definition
- Ingest APIs
    - Put Pipeline API
    - Get Pipeline API
    - Delete Pipeline API
    - Simulate Pipeline API
- Accessing Data in Pipelines
- Conditional Execution in Pipelines
    - Handling Nested Fields in Conditionals
    - Complex Conditionals
    - Conditionals with the Pipeline Processor
    - Conditionals with the Regular Expressions
- Handling Failures in Pipelines
- Processors
    - Append Processor
    - Bytes Processor
    - Convert Processor
    - Date Processor
    - Date Index Name Processor
    - Dissect Processor
    - Drop Processor
    - Dot Expander Processor
    - Fail Processor
    - Foreach Processor
    - Grok Processor
    - Gsub Processor
    - Join Processor
    - JSON Processor
    - KV Processor
    - Lowercase Processor
    - Pipeline Processor
    - Remove Processor
    - Rename Processor
    - Script Processor
    - Set Processor
    - Set Security User Processor
    - Split Processor
    - Sort Processor
    - Trim Processor
    - Uppercase Processor
    - URL Decode Processor

## Managing the index lifecycle
- Getting started with index lifecycle management
    - Setting up a new policy
    - Applying a policy to our index
    - Checking progress
- Policy phases and actions
    - Timing
    - Phase Execution
    - Actions
    - Full Policy
- Set up index lifecycle management policy
    - Applying a policy to an index template
    - Apply a policy to a create index request
- Using policies to manage index rollover
    - Skipping Rollover
- Update policy
    - Updates to policies not managing indices
    - Updates to executing policies
    - Switching policies for an index
- Index lifecycle error handling
- Restoring snapshots of managed indices
- Start and stop index lifecycle management

## SQL Access
- Overview
- Getting Started with SQL
- Conventions and Terminology
    - Mapping concepts across SQL and Elasticsearch
- Security
- SQL REST API
- SQL Translate API
- SQL CLI
- SQL JDBC
    - API usage
- SQL ODBC
    - Driver installation
    - Configuration
- SQL Client Applications
    - DBeaver
    - DbVisualizer
    - Microsoft Excel
    - Microsoft Power BI Desktop
    - Microsoft PowerShell
    - MicroStrategy Desktop
    - Qlik Sense Desktop
    - SQuirreL SQL
    - Tableau Desktop
    - SQL Workbench/J
- SQL Language
- Data Types
- SQL Commands
    - DESCRIBE TABLE
    - SELECT
    - SHOW COLUMNS
    - SHOW FUNCTIONS
    - SHOW TABLES
- Index patterns
- Functions and Operators
    - Comparison Operators
    - Logical Operators
    - Math Operators
    - Aggregate Functions
    - Grouping Functions
    - Date/Time and Interval Functions and Operators
    - Full-Text Search Functions
    - Math Functions
    - String Functions
    - Type Conversion Functions
    - Conditional Functions
    - System Functions
- Reserved keywords
- SQL Limitations

## Monitoring Elasticsearch
- Collectors
- Exporters
    - Local Exporters
    - HTTP Exporters
- Pausing Data Collection

## Rolling up historical data
- Overview
- API Quick Reference
- Getting Started
- Understanding Groups
    - Grouping Limitations with heterogeneous indices
    - Doc counts and overlapping jobs
- Rollup Aggregation Limitations
- Rollup Search Limitations

## Frozen Indices
- Best Practices
- Searching a frozen index

## X-Pack APIs
- Info API
- Cross-cluster replication APIs
    - Get CCR stats
    - Create follower
    - Pause follower
    - Resume follower
    - Unfollow
    - Get follower stats
    - Create auto-follow pattern
    - Delete auto-follow pattern
    - Get auto-follow pattern
- Explore API
- Freeze index
- Index lifecycle management API
    - Create policy
    - Get policy
    - Delete policy
    - Move to step
    - Remove policy
    - Retry policy
    - Get index lifecycle management status
    - Explain lifecycle
    - Start index lifecycle management
    - Stop index lifecycle management
- Licensing APIs
    - Delete license
    - Get license
    - Get trial status
    - Start trial
    - Get basic status
    - Start basic
    - Update license
- Migration APIs
    - Migration assistance
    - Migration upgrade
    - Deprecation info
- Machine learning APIs
    - Add events to calendar
    - Add jobs to calendar
    - Close jobs
    - Create calendar
    - Create datafeeds
    - Create filter
    - Create jobs
    - Delete calendar
    - Delete datafeeds
    - Delete events from calendar
    - Delete filter
    - Delete forecast
    - Delete jobs
    - Delete jobs from calendar
    - Delete model snapshots
    - Delete expired data
    - Find file structure
    - Flush jobs
    - Forecast jobs
    - Get calendars
    - Get buckets
    - Get overall buckets
    - Get categories
    - Get datafeeds
    - Get datafeed statistics
    - Get influencers
    - Get jobs
    - Get job statistics
    - Get machine learning info
    - Get model snapshots
    - Get scheduled events
    - Get filters
    - Get records
    - Open jobs
    - Post data to jobs
    - Preview datafeeds
    - Revert model snapshots
    - Start datafeeds
    - Stop datafeeds
    - Update datafeeds
    - Update filter
    - Update jobs
    - Update model snapshots
- Rollup APIs
    - Delete job
    - Get job
    - Create job
    - Start job
    - Stop job
    - Get rollup caps
    - Get rollup index caps
    - Rollup search
    - Rollup job configuration
- Security APIs
    - Authenticate
    - Change passwords
    - Clear cache
    - Clear roles cache
    - Create or update application privileges
    - Create or update role mappings
    - Create or update roles
    - Create or update users
    - Delete application privileges
    - Delete role mappings
    - Delete roles
    - Delete users
    - Disable users
    - Enable users
    - Get application privileges
    - Get role mappings
    - Get roles
    - Get token
    - Get users
    - Has privileges
    - Invalidate token
    - SSL certificate
- Unfreeze index
- Watcher APIs
    - Put watch
    - Get watch
    - Delete watch
    - Execute watch
    - Ack watch
    - Activate watch
    - Deactivate watch
    - Stats
    - Stop
    - Start
    - Restart API
- Definitions
    - Calendar resources
    - Datafeed resources
    - Filter resources
    - Job resources
    - Job statistics
    - Model snapshot resources
    - Role mapping resources
    - Results resources
    - Scheduled event resources

## Command line tools
- elasticsearch-certgen
- elasticsearch-certutil
- elasticsearch-migrate
- elasticsearch-saml-metadata
- elasticsearch-setup-passwords
- elasticsearch-shard
- elasticsearch-syskeygen
- elasticsearch-users

## How To
- General recommendations
- Recipes
    - Mixing exact search with stemming
    - Getting consistent scoring
- Tune for indexing speed
- Tune for search speed
- Tune for disk usage

## Testing
- Java Testing Framework
    - Why randomized testing?
    - Using the Elasticsearch test classes
    - unit tests
    - Integration tests
    - Randomized testing
    - Assertions
