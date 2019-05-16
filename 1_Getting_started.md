## [[1] Getting started](https://www.elastic.co/guide/en/elasticsearch/reference/current/getting-started.html)

Elasticsearch is a highly scalable open-source full-text search and analytics engine. It allows you to store, search, and analyze big volumes of data quickly and in near real time. It is generally used as the underlying engine/technology that powers applications that have complex search features and requirements.  
Elasticsearch는 확장성이 뛰어난 오픈 소스 전체 텍스트 검색 및 분석 엔진이다. 대용량 데이터를 빠르고 실시간으로 저장, 검색 및 분석할 수 있다. 그것은 일반적으로 복잡한 검색 기능과 요구 사항을 가진 어플리케이션에 전력을 공급하는 기반 엔진/기술로 사용된다.

Here are a few sample use-cases that Elasticsearch could be used for:  
다음은 Elasticsearch를 사용할 수 있는 몇 가지 샘플 사용 사례입니다.

- You run an online web store where you allow your customers to search for products that you sell. In this case, you can use Elasticsearch to store your entire product catalog and inventory and provide search and autocomplete suggestions for them.
- 당신은 당신이 판매하는 제품을 당신의 고객이 검색하도록 허용하는 온라인 웹 상점을 운영한다. 이 경우 Elasticsearch를 사용하여 전체 제품 카탈로그와 인벤토리를 저장하고 검색 및 자동 완성 제안을 제공할 수 있다.

+ You want to collect log or transaction data and you want to analyze and mine this data to look for trends, statistics, summarizations, or anomalies. In this case, you can use Logstash (part of the Elasticsearch/Logstash/Kibana stack) to collect, aggregate, and parse your data, and then have Logstash feed this data into Elasticsearch. Once the data is in Elasticsearch, you can run searches and aggregations to mine any information that is of interest to you.
+ 로그 또는 트랜잭션 데이터를 수집하고 이 데이터를 분석하고 채굴하여 추세, 통계, 요약 또는 이상 징후를 찾으려는 경우. 이 경우 Logstash(Elasticsearch/Logstash/Kibana 스택의 일부)를 사용하여 데이터를 수집, 집계 및 구문 분석한 다음 Logstash가 이 데이터를 Elasticsearch에 입력하도록 할 수 있다. 데이터가 Elasticsearch에 저장되면 검색 및 집계를 실행하여 관심 있는 모든 정보를 수집할 수 있다.

- You run a price alerting platform which allows price-savvy customers to specify a rule like "I am interested in buying a specific electronic gadget and I want to be notified if the price of gadget falls below $X from any vendor within the next month". In this case you can scrape vendor prices, push them into Elasticsearch and use its reverse-search (Percolator) capability to match price movements against customer queries and eventually push the alerts out to the customer once matches are found.
- 당신은 가격에 정통한 고객들이 "나는 특정 전자 기기를 사는 데 관심이 있고 다음 달 안에 어떤 판매 업체로부터도 기기 가격이 X달러 미만으로 떨어지면 통보를 받고 싶다"와 같은 규칙을 정할 수 있도록 하는 가격 경보 플랫폼을 운영하고 있다. 이 경우 공급업체 가격을 긁어모으고, 이를 Elasticsearch에 밀어넣고, 그 역검색(Percolator) 기능을 사용하여 고객 쿼리에 대한 가격 이동을 일치시키고, 결국 일치 항목이 발견되면 고객에게 경고를 내보낼 수 있다.

+ You have analytics/business-intelligence needs and want to quickly investigate, analyze, visualize, and ask ad-hoc questions on a lot of data (think millions or billions of records). In this case, you can use Elasticsearch to store your data and then use Kibana (part of the Elasticsearch/Logstash/Kibana stack) to build custom dashboards that can visualize aspects of your data that are important to you. Additionally, you can use the Elasticsearch aggregations functionality to perform complex business intelligence queries against your data.
+ 분석/비즈니스 인텔리전스 요구사항을 가지고 있으며 많은 데이터에 대해 신속하게 조사, 분석, 시각화 및 임시 질문(수백만 또는 수십억 개의 기록을 생각해 보십시오)하고 싶어 한다. 이 경우 Elasticsearch를 사용하여 데이터를 저장한 다음 Kibana(Elasticsearch/Logstash/Kibana stack의 일부)를 사용하여 자신에게 중요한 데이터의 측면을 시각화할 수 있는 사용자 지정 대시보드를 구축할 수 있다. 또한 ElasticSearch Aggregation 기능을 사용하여 데이터에 대해 복잡한 비즈니스 인텔리전스 쿼리를 수행할 수 있다.

For the rest of this tutorial, you will be guided through the process of getting Elasticsearch up and running, taking a peek inside it, and performing basic operations like indexing, searching, and modifying your data. At the end of this tutorial, you should have a good idea of what Elasticsearch is, how it works, and hopefully be inspired to see how you can use it to either build sophisticated search applications or to mine intelligence from your data.  
이 튜토리얼의 나머지 부분에 대해서는 Elasticsearch를 가동하고, 그 안을 들여다보고, 데이터 인덱싱, 검색, 수정과 같은 기본적인 작업을 수행하는 과정을 안내받을 것이다. 이 튜토리얼이 끝날 때, 여러분은 Elasticsearch가 무엇인지, 어떻게 작동하는지 잘 알고 있어야 하며, 어떻게 이것을 사용하여 정교한 검색 응용 프로그램을 구축하거나 데이터에서 지능을 채굴할 수 있는지에 대해 영감을 얻기를 바란다.

### [1-1. Basic Concepts](https://www.elastic.co/guide/en/elasticsearch/reference/current/getting-started-concepts.html)

There are a few concepts that are core to Elasticsearch. Understanding these concepts from the outset will tremendously help ease the learning process.  
Elasticsearch의 핵심이 되는 몇 가지 개념이 있다. 이러한 개념을 처음부터 이해하는 것은 학습 과정을 용이하게 하는데 크게 도움이 될 것이다.

**Near Realtime (NRT)**  
Elasticsearch is a near-realtime search platform. What this means is there is a slight latency (normally one second) from the time you index a document until the time it becomes searchable.  
Elasticsearch는 거의 실시간에 가까운 검색 플랫폼이다. 이것은 document를 index할 때부터 검색 가능해질 때까지 약간의 지연 시간(일반적으로 1초)이 있다는 것을 의미한다.

**Cluster**  
A cluster is a collection of one or more nodes (servers) that together holds your entire data and provides federated indexing and search capabilities across all nodes. A cluster is identified by a unique name which by default is "elasticsearch". This name is important because a node can only be part of a cluster if the node is set up to join the cluster by its name.  
클러스터는 전체 데이터를 함께 보관하고 모든 노드에서 통합 인덱싱 및 검색 기능을 제공하는 하나 이상의 노드(서버)의 모음입니다. 클러스터는 기본적으로 "elasticsearch"인 고유한 이름으로 식별된다. 노드가 이름으로 클러스터에 가입하도록 설정된 경우에만 노드가 클러스터의 일부가 될 수 있기 때문에 이 이름은 중요하다.

Make sure that you don’t reuse the same cluster names in different environments, otherwise you might end up with nodes joining the wrong cluster. For instance you could use `logging-dev`, `logging-stage`, and `logging-prod` for the development, staging, and production clusters.  
다른 환경에서 동일한 클러스터 이름을 재사용하지 마십시오. 그렇지 않으면 노드가 잘못된 클러스터에 가입할 수 있습니다. 예를 들어 개발, 스테이징 및 프로덕션 클러스터에 `logging-dev`, `logging-stage` 및 `logging-prod`를 사용할 수 있다.

Note that it is valid and perfectly fine to have a cluster with only a single node in it. Furthermore, you may also have multiple independent clusters each with its own unique cluster name.  
단일 노드만 포함된 클러스터를 사용하는 것은 타당하고 완벽하다는 점에 유의하십시오. 또한 각각 고유한 클러스터 이름을 가진 독립 클러스터가 여러 개 있을 수 있다.

**Node**  
A node is a single server that is part of your cluster, stores your data, and participates in the cluster’s indexing and search capabilities. Just like a cluster, a node is identified by a name which by default is a random Universally Unique IDentifier (UUID) that is assigned to the node at startup. You can define any node name you want if you do not want the default. This name is important for administration purposes where you want to identify which servers in your network correspond to which nodes in your Elasticsearch cluster.  
노드는 클러스터의 일부분이고 데이터를 저장하며 클러스터의 인덱싱 및 검색 기능에 참여하는 단일 서버입니다. 클러스터와 마찬가지로, 노드는 시작할 때 노드에 할당되는 임의 UUID(Universally Unique IDentifier)로 식별된다. 기본값을 원하지 않는 경우 원하는 노드 이름을 정의할 수 있다. 이 이름은 네트워크에서 Elasticsearch 클러스터의 노드에 해당하는 서버를 식별하려는 관리 목적으로 중요하다.

A node can be configured to join a specific cluster by the cluster name. By default, each node is set up to join a cluster named `elasticsearch` which means that if you start up a number of nodes on your network and—assuming they can discover each other—they will all automatically form and join a single cluster named `elasticsearch`.  
클러스터 이름으로 특정 클러스터에 가입하도록 노드를 구성할 수 있다. 기본적으로, 각 노드는 `elasticsearch`이라는 이름의 클러스터에 가입하도록 설정되며, 이는 네트워크에서 여러 노드를 시작하고 서로 검색할 수 있다고 가정할 때 모두 자동으로 `elasticsearch`이라는 단일 클러스터를 형성하고 결합한다는 것을 의미한다.

In a single cluster, you can have as many nodes as you want. Furthermore, if there are no other Elasticsearch nodes currently running on your network, starting a single node will by default form a new single-node cluster named `elasticsearch`.    
단일 클러스터에서 원하는 만큼의 노드를 가질 수 있다. 또한 현재 네트워크에서 실행 중인 다른 Elasticsearch 노드가 없는 경우, 기본적으로 단일 노드를 시작하면 `elasticsearch`이라는 새로운 단일 노드 클러스터가 형성된다.

**Index**  
An index is a collection of documents that have somewhat similar characteristics. For example, you can have an index for customer data, another index for a product catalog, and yet another index for order data. An index is identified by a name (that must be all lowercase) and this name is used to refer to the index when performing indexing, search, update, and delete operations against the documents in it.    
index는 다소 유사한 특성을 가진 document의 집합이다. 예를 들어 고객 데이터에 대한 index, 제품 카탈로그에 대한 다른 index 및 주문 데이터에 대한 index를 가질 수 있다. index는 이름(모두 소문자여야 함)으로 식별되며, 이 이름은 해당 문서에 대한 indexing, 검색, 업데이트 및 삭제 작업을 수행할 때 index를 참조하는 데 사용된다.

In a single cluster, you can define as many indexes as you want.  
단일 클러스터에서 원하는 만큼의 index를 정의할 수 있다.

**Type** `❗Deprecated in 6.0.0.❗`  
A type used to be a logical category/partition of your index to allow you to store different types of documents in the same index, e.g. one type for users, another type for blog posts. It is no longer possible to create multiple types in an index, and the whole concept of types will be removed in a later version. See [Removal of mapping types](https://www.elastic.co/guide/en/elasticsearch/reference/current/removal-of-types.html) for more.  
다른 type의 document를 동일한 index에 저장할 수 있도록 하기 위해 index의 논리 카테고리/파티션으로 사용되는 type (예: 사용자를 위한 type, 블로그 게시물의 type) 더 이상 index에서 여러 type을 만들 수 없으며, type에 대한 전체 개념은 이후 버전에서 제거될 것이다. 자세한 내용은 매핑 type 제거를 참조하십시오.

**Document**  
A document is a basic unit of information that can be indexed. For example, you can have a document for a single customer, another document for a single product, and yet another for a single order. This document is expressed in [JSON](http://json.org/) (JavaScript Object Notation) which is a ubiquitous internet data interchange format. Within an index, you can store as many documents as you want.  
document는 index 할 수 있는 정보의 기본 단위다. 예를 들어 단일 고객을 위한 document, 단일 제품을 위한 다른 document, 단일 주문을 위한 다른 document를 가질 수 있다. 이 document는 유비쿼터스 인터넷 데이터 교환 형식인 [JSON](http://json.org/) (JavaScript Object Notation)으로 표현되어 있다. index 내에서 원하는 만큼의 document를 저장할 수 있다.

**Shards & Replicas**  
An index can potentially store a large amount of data that can exceed the hardware limits of a single node. For example, a single index of a billion documents taking up 1TB of disk space may not fit on the disk of a single node or may be too slow to serve search requests from a single node alone.  
index는 단일 노드의 하드웨어 한계를 초과할 수 있는 대량의 데이터를 저장할 수 있다. 예를 들어 1TB의 디스크 공간을 차지하는 10억 개의 문서의 단일 index는 단일 노드의 디스크에 맞지 않거나 단일 노드에서만 검색 요청을 처리하기에는 너무 느릴 수 있다.

To solve this problem, Elasticsearch provides the ability to subdivide your index into multiple pieces called shards. When you create an index, you can simply define the number of shards that you want. Each shard is in itself a fully-functional and independent "index" that can be hosted on any node in the cluster.  
이 문제를 해결하기 위해, Elasticsearch는 당신의 index를 shard라고 불리는 여러 조각으로 세분화하는 기능을 제공한다. index를 작성할 때 원하는 shard의 개수를 간단히 정의할 수 있다. 각 shard는 그 자체로 클러스터의 모든 노드에서 호스팅할 수 있는 완전히 기능하고 독립적인 "index"이다.

Sharding is important for two primary reasons:  
Sharding은 두 가지 주요 이유로 중요하다.

- It allows you to horizontally split/scale your content volume
- 콘텐츠 볼륨을 수평으로 분할/스케일링할 수 있음

+ It allows you to distribute and parallelize operations across shards (potentially on multiple nodes) thus increasing performance/throughput
+ 여러 노드에 걸쳐 운영 방식을 분산 및 병렬화할 수 있으므로 성능/처리 성능 향상

The mechanics of how a shard is distributed and also how its documents are aggregated back into search requests are completely managed by Elasticsearch and is transparent to you as the user.  
shard가 배포되는 방법과 그 document가 검색 요청으로 다시 집계되는 방법은 Elasticsearch에 의해 완전히 관리되며 사용자로서 사용자에게 투명하다.

In a network/cloud environment where failures can be expected anytime, it is very useful and highly recommended to have a failover mechanism in case a shard/node somehow goes offline or disappears for whatever reason. To this end, Elasticsearch allows you to make one or more copies of your index’s shards into what are called replica shards, or replicas for short.  
언제든지 장애를 예상할 수 있는 네트워크/클라우드 환경에서는 shard/노드가 어떻게든 오프라인 상태가 되거나 어떤 이유로든 사라질 경우 페일오버 메커니즘을 갖는 것이 매우 유용하고 매우 권장된다. 이를 위해, Elasticsearch를 사용하면 index의 shard들을 replica shards 또는 줄여서 replicas라고 하는 것으로 복사할 수 있다.

Replication is important for two primary reasons:  
복제는 두 가지 주요 이유로 중요하다.

- It provides high availability in case a shard/node fails. For this reason, it is important to note that a replica shard is never allocated on the same node as the original/primary shard that it was copied from.
- shard/노드가 고장 날 경우 고가용성을 제공한다. 이 때문에 replica shard는 복사된 original/primary shard와 동일한 노드에 할당되지 않는다는 점에 유의해야 한다.

+ It allows you to scale out your search volume/throughput since searches can be executed on all replicas in parallel.
+ 검색을 모든 replicas에서 병렬로 실행할 수 있으므로 검색 볼륨/처리량을 확장할 수 있다.

To summarize, each index can be split into multiple shards. An index can also be replicated zero (meaning no replicas) or more times. Once replicated, each index will have primary shards (the original shards that were replicated from) and replica shards (the copies of the primary shards).  
요약하자면, 각 index를 여러 개의 shard로 나눌 수 있다. index는 0번(replica 없음) 이상 복제할 수도 있다. 일단 복제되면, 각 index는 primary shards(복제된 원래 shard)와 replica shards(primary shard의 복사본)를 가질 것이다.

The number of shards and replicas can be defined per index at the time the index is created. After the index is created, you may also change the number of replicas dynamically anytime. You can change the number of shards for an existing index using the [`_shrink`](https://www.elastic.co/guide/en/elasticsearch/reference/7.0/indices-shrink-index.html) and [`_split`](https://www.elastic.co/guide/en/elasticsearch/reference/7.0/indices-split-index.html) APIs, however this is not a trivial task and pre-planning for the correct number of shards is the optimal approach.  
index가 작성될 때 index별로 shard와 replica의 수를 정의할 수 있다. index가 생성된 후에는 언제든지 동적으로 replica 수를 변경할 수도 있다. `_shrink` 및 `_split` API를 사용하여 기존 index의 shard 수를 변경할 수 있지만, 이는 사소한 작업이 아니며 정확한 shard 수에 대한 사전 계획이 최적의 접근방식이다.

By default, each index in Elasticsearch is allocated one primary shard and one replica which means that if you have at least two nodes in your cluster, your index will have one primary shard and another replica shard (one complete replica) for a total of two shards per index.  
기본적으로 Elasticsearch의 각 index는 하나의 기본 shard와 하나의 replica가 할당되는데, 이는 클러스터에 적어도 두 개 이상의 노드가 있을 경우 index는 index당 총 두 개의 shard를 위해 하나의 primary shard와 다른 replica shard(하나의 완전한 replica)를 가질 것이다.

> **Note**  
> Each Elasticsearch shard is a Lucene index. There is a maximum number of documents you can have in a single Lucene index. As of [LUCENE-5843](https://issues.apache.org/jira/browse/LUCENE-5843), the limit is 2,147,483,519 (= Integer.MAX_VALUE - 128) documents. You can monitor shard sizes using the [_cat/shards](https://www.elastic.co/guide/en/elasticsearch/reference/7.0/cat-shards.html) API.  
> 각각의 Elasticsearch 샤드는 Lucene index이다. 단일 Lucene index에서 가질 수 있는 document의 최대 개수가 있다. LUCENE-5843 기준으로 한계는 2,147,483,519(= Integer.MAX_VALUE - 128) document 이다. _cat/shards API를 사용하여 샤드 크기를 모니터링할 수 있다.

With that out of the way, let’s get started with the fun part…  
그 점을 벗어나서 재미있는 부분부터 시작해보자...

### [1-2. Installation](https://www.elastic.co/guide/en/elasticsearch/reference/current/getting-started-install.html)

> **Tip**  
> You can skip having to install Elasticsearch by using our [hosted Elasticsearch Service](https://www.elastic.co/kr/cloud/elasticsearch-service) on Elastic Cloud. The Elasticsearch Service is available on both AWS and GCP. [Try out the Elasticsearch Service for free](https://www.elastic.co/kr/cloud/elasticsearch-service/signup).  
> Elastic Cloud에 호스팅된 Elasticsearch 서비스를 사용하면 Elasticsearch를 설치하지 않아도 된다. Elasticsearch 서비스는 AWS와 GCP 모두에서 이용 가능하다. Elastic Search 서비스를 무료로 사용해 보십시오.

> **Note**  
> Elasticsearch includes a bundled version of [OpenJDK](http://openjdk.java.net/) from the JDK maintainers (GPLv2+CE). To use your own version of Java, see the [JVM version requirements](https://www.elastic.co/guide/en/elasticsearch/reference/current/setup.html#jvm-version)   
> Elasticsearch는 JDK maintainers(GPLv2+CE)의 OpenJDK 번들 버전을 포함한다. 사용자 자신의 Java 버전을 사용하려면 JVM 버전 요구 사항을 참조하십시오.

The binaries are available from [www.elastic.co/downloads](https://www.elastic.co/kr/downloads/) along with all the releases that have been made in the past. For each release, platform dependent archive versions are available for Windows, Linux and MacOS, as well as DEB and RPM packages for Linux, and MSI installation packages for Windows.  
이 바이너리는 과거에 만들어진 모든 릴리스와 함께 www.elastic.co/downloads에서 이용할 수 있다. 각 릴리스에 대해 플랫폼 종속 아카이브 버전은 Windows, Linux 및 MacOS, Linux용 DEB 및 RPM 패키지 및 Windows용 MSI 설치 패키지에 사용할 수 있다.

**Installation example on Linux**  
For simplicity, let’s use the [tar](https://www.elastic.co/guide/en/elasticsearch/reference/7.0/targz.html) file.
단순성을 위해 tar 파일을 사용합시다.

Let’s download the Elasticsearch 7.0.1 Linux tar as follows:  
다음과 같이 Elasticsearch 7.0.1 Linux tar를 다운로드하십시오.

```bash
curl -L -O https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.0.1-linux-x86_64.tar.gz
```

Then extract it as follows:  
그런 다음 다음과 같이 추출한다.

```bash
tar -xvf elasticsearch-7.0.1-linux-x86_64.tar.gz
```

It will then create a bunch of files and folders in your current directory. We then go into the bin directory as follows:  
그러면 현재 디렉토리에 파일과 폴더 묶음이 만들어질 것이다. 그런 다음 다음과 같이 bin 디렉토리로 들어간다.

```bash
cd elasticsearch-7.0.1/bin
```

And now we are ready to start our node and single cluster:  
이제 노드와 단일 클러스터를 시작할 준비가 완료됨:

```
./elasticsearch
```

~~**Installation example with MSI Windows Installer**~~ ⚠

**Successfully running node**  
If everything goes well with installation, you should see a bunch of messages that look like below:  
모든 것이 설치와 잘 되면 다음과 같은 여러 메시지가 표시되어야 한다.

```bash
[2018-09-13T12:20:01,766][INFO ][o.e.e.NodeEnvironment    ] [localhost.localdomain] using [1] data paths, mounts [[/home (/dev/mapper/fedora-home)]], net usable_space [335.3gb], net total_space [410.3gb], types [ext4]
[2018-09-13T12:20:01,772][INFO ][o.e.e.NodeEnvironment    ] [localhost.localdomain] heap size [990.7mb], compressed ordinary object pointers [true]
[2018-09-13T12:20:01,774][INFO ][o.e.n.Node               ] [localhost.localdomain] node name [localhost.localdomain], node ID [B0aEHNagTiWx7SYj-l4NTw]
[2018-09-13T12:20:01,775][INFO ][o.e.n.Node               ] [localhost.localdomain] version[7.0.1], pid[13030], build[oss/zip/77fc20e/2018-09-13T15:37:57.478402Z], OS[Linux/4.16.11-100.fc26.x86_64/amd64], JVM["Oracle Corporation"/OpenJDK 64-Bit Server VM/10/10+46]
[2018-09-13T12:20:01,775][INFO ][o.e.n.Node               ] [localhost.localdomain] JVM arguments [-Xms1g, -Xmx1g, -XX:+UseConcMarkSweepGC, -XX:CMSInitiatingOccupancyFraction=75, -XX:+UseCMSInitiatingOccupancyOnly, -XX:+AlwaysPreTouch, -Xss1m, -Djava.awt.headless=true, -Dfile.encoding=UTF-8, -Djna.nosys=true, -XX:-OmitStackTraceInFastThrow, -Dio.netty.noUnsafe=true, -Dio.netty.noKeySetOptimization=true, -Dio.netty.recycler.maxCapacityPerThread=0, -Dlog4j.shutdownHookEnabled=false, -Dlog4j2.disable.jmx=true, -Djava.io.tmpdir=/tmp/elasticsearch.LN1ctLCi, -XX:+HeapDumpOnOutOfMemoryError, -XX:HeapDumpPath=data, -XX:ErrorFile=logs/hs_err_pid%p.log, -Xlog:gc*,gc+age=trace,safepoint:file=logs/gc.log:utctime,pid,tags:filecount=32,filesize=64m, -Djava.locale.providers=COMPAT, -XX:UseAVX=2, -Dio.netty.allocator.type=unpooled, -Des.path.home=/home/manybubbles/Workspaces/Elastic/master/elasticsearch/qa/unconfigured-node-name/build/cluster/integTestCluster node0/elasticsearch-7.0.0-alpha1-SNAPSHOT, -Des.path.conf=/home/manybubbles/Workspaces/Elastic/master/elasticsearch/qa/unconfigured-node-name/build/cluster/integTestCluster node0/elasticsearch-7.0.0-alpha1-SNAPSHOT/config, -Des.distribution.flavor=oss, -Des.distribution.type=zip]
[2018-09-13T12:20:02,543][INFO ][o.e.p.PluginsService     ] [localhost.localdomain] loaded module [aggs-matrix-stats]
[2018-09-13T12:20:02,543][INFO ][o.e.p.PluginsService     ] [localhost.localdomain] loaded module [analysis-common]
[2018-09-13T12:20:02,543][INFO ][o.e.p.PluginsService     ] [localhost.localdomain] loaded module [ingest-common]
[2018-09-13T12:20:02,544][INFO ][o.e.p.PluginsService     ] [localhost.localdomain] loaded module [lang-expression]
[2018-09-13T12:20:02,544][INFO ][o.e.p.PluginsService     ] [localhost.localdomain] loaded module [lang-mustache]
[2018-09-13T12:20:02,544][INFO ][o.e.p.PluginsService     ] [localhost.localdomain] loaded module [lang-painless]
[2018-09-13T12:20:02,544][INFO ][o.e.p.PluginsService     ] [localhost.localdomain] loaded module [mapper-extras]
[2018-09-13T12:20:02,544][INFO ][o.e.p.PluginsService     ] [localhost.localdomain] loaded module [parent-join]
[2018-09-13T12:20:02,544][INFO ][o.e.p.PluginsService     ] [localhost.localdomain] loaded module [percolator]
[2018-09-13T12:20:02,544][INFO ][o.e.p.PluginsService     ] [localhost.localdomain] loaded module [rank-eval]
[2018-09-13T12:20:02,544][INFO ][o.e.p.PluginsService     ] [localhost.localdomain] loaded module [reindex]
[2018-09-13T12:20:02,545][INFO ][o.e.p.PluginsService     ] [localhost.localdomain] loaded module [repository-url]
[2018-09-13T12:20:02,545][INFO ][o.e.p.PluginsService     ] [localhost.localdomain] loaded module [transport-netty4]
[2018-09-13T12:20:02,545][INFO ][o.e.p.PluginsService     ] [localhost.localdomain] no plugins loaded
[2018-09-13T12:20:04,657][INFO ][o.e.d.DiscoveryModule    ] [localhost.localdomain] using discovery type [zen]
[2018-09-13T12:20:05,006][INFO ][o.e.n.Node               ] [localhost.localdomain] initialized
[2018-09-13T12:20:05,007][INFO ][o.e.n.Node               ] [localhost.localdomain] starting ...
[2018-09-13T12:20:05,202][INFO ][o.e.t.TransportService   ] [localhost.localdomain] publish_address {127.0.0.1:9300}, bound_addresses {[::1]:9300}, {127.0.0.1:9300}
[2018-09-13T12:20:05,221][WARN ][o.e.b.BootstrapChecks    ] [localhost.localdomain] max file descriptors [4096] for elasticsearch process is too low, increase to at least [65535]
[2018-09-13T12:20:05,221][WARN ][o.e.b.BootstrapChecks    ] [localhost.localdomain] max virtual memory areas vm.max_map_count [65530] is too low, increase to at least [262144]
[2018-09-13T12:20:08,384][INFO ][o.e.h.n.Netty4HttpServerTransport] [localhost.localdomain] publish_address {127.0.0.1:9200}, bound_addresses {[::1]:9200}, {127.0.0.1:9200}
[2018-09-13T12:20:08,384][INFO ][o.e.n.Node               ] [localhost.localdomain] started
```

Without going too much into detail, we can see that our node named "6-bjhwl" (which will be a different set of characters in your case) has started and elected itself as a master in a single cluster. Don’t worry yet at the moment what master means. The main thing that is important here is that we have started one node within one cluster.  
너무 자세히 설명하지 않아도, "6-bjhwl"(당신의 경우 다른 문자 집합이 될 것)이라는 이름의 우리의 노드가 시작되어 단일 클러스터에서 마스터로 선출되었음을 알 수 있다. 마스터의 뜻이 무슨 뜻인지 현재로서는 아직 걱정하지 마라. 여기서 중요한 것은 하나의 클러스터 내에서 하나의 노드를 시작했다는 것이다.

As mentioned previously, we can override either the cluster or node name. This can be done from the command line when starting Elasticsearch as follows:  
앞에서 언급한 바와 같이 클러스터 또는 노드 이름을 재정의할 수 있다. 이는 다음과 같이 Elasticsearch를 시작할 때 명령줄에서 수행할 수 있다.

```bash
./elasticsearch -Ecluster.name=my_cluster_name -Enode.name=my_node_name
```

Also note the line marked http with information about the HTTP address (192.168.8.112) and port (9200) that our node is reachable from. By default, Elasticsearch uses port 9200 to provide access to its REST API. This port is configurable if necessary.  
또한 http로 표시된 행에 노드가 연결할 수 있는 HTTP 주소(192.168.8.112) 및 포트(9200)에 대한 정보를 기록하십시오. 기본적으로 Elasticsearch는 포트 9200을 사용하여 REST API에 대한 액세스를 제공한다. 이 포트는 필요한 경우 구성할 수 있다.

### [1-3. Exploring Your Cluster](https://www.elastic.co/guide/en/elasticsearch/reference/7.x/getting-started-explore.html)

**The REST API**

Now that we have our node (and cluster) up and running, the next step is to understand how to communicate with it. Fortunately, Elasticsearch provides a very comprehensive and powerful REST API that you can use to interact with your cluster. Among the few things that can be done with the API are as follows:  
이제 노드(및 클러스터)를 가동하고 실행하고 있으므로 다음 단계는 노드와의 통신 방법을 이해하는 것이다. 다행히도 Elasticsearch는 클러스터와 상호 작용하는 데 사용할 수 있는 매우 포괄적이고 강력한 REST API를 제공한다. API로 할 수 있는 몇 가지 일 중 다음과 같은 것이 있다.

- Check your cluster, node, and index health, status, and statistics
- 클러스터, 노드 및 인덱스 상태, 상태 및 통계 확인

+ Administer your cluster, node, and index data and metadata
+ 클러스터, 노드 및 인덱스 데이터 및 메타데이터 관리

- Perform CRUD (Create, Read, Update, and Delete) and search operations against your indexes
- 인덱스에 대해 CRUD(생성, 읽기, 업데이트 및 삭제) 및 검색 작업 수행

+ Execute advanced search operations such as paging, sorting, filtering, scripting, aggregations, and many others
+ 페이징, 정렬, 필터링, 스크립팅, 집계 등의 고급 검색 작업 실행

#### [1-3-1) Cluster Health](https://www.elastic.co/guide/en/elasticsearch/reference/7.x/getting-started-cluster-health.html)

Let’s start with a basic health check, which we can use to see how our cluster is doing. We’ll be using curl to do this but you can use any tool that allows you to make HTTP/REST calls. Let’s assume that we are still on the same node where we started Elasticsearch on and open another command shell window.  
먼저 클러스터가 어떻게 작동하는지 확인할 수 있는 기본 상태 점검부터 시작합시다. 이를 위해 curl을 사용할 것이지만 HTTP/REST를 호출 할 수 있는 모든 도구를 사용할 수 있다. 우리가 여전히 Elasticsearch on을 시작하고 다른 명령 셸 창을 열었던 동일한 노드에 있다고 가정하자.


To check the cluster health, we will be using the [`_cat` API](https://www.elastic.co/guide/en/elasticsearch/reference/7.x/cat.html). You can run the command below in [Kibana’s Console](https://www.elastic.co/guide/en/kibana/7.x/console-kibana.html) by clicking "VIEW IN CONSOLE" or with `curl` by clicking the "COPY AS CURL" link below and pasting it into a terminal.  
클러스터 상태를 확인하기 위해 `_cat API`를 사용할 것이다. 아래의 명령을 키바나의 콘솔에서 "VIEW IN CONSOLE"을 클릭하거나 아래의 "COPY AS CURL" 링크를 클릭하여 터미널에 붙여넣으면 실행할 수 있다.

```bash
GET /_cat/health?v
```

And the response:  
그리고 응답:

```bash
epoch      timestamp cluster       status node.total node.data shards pri relo init unassign pending_tasks max_task_wait_time active_shards_percent
1475247709 17:01:49  elasticsearch green           1         1      0   0    0    0        0             0                  -                100.0%
```

We can see that our cluster named "elasticsearch" is up with a green status.  
우리는 "elasticsearch"라는 이름의 클러스터가 녹색 상태를 유지하고 있다는 것을 알 수 있다.

Whenever we ask for the cluster health, we either get green, yellow, or red.  
클러스터 상태를 요청할 때마다 녹색, 노란색 또는 빨간색 중 하나가 된다.

- Green - everything is good (cluster is fully functional)
- Green - 모든 것이 양호함 (클러스터가 완전히 작동함)

+ Yellow - all data is available but some replicas are not yet allocated (cluster is fully functional)
+ Yellow - 모든 데이터를 사용할 수 있지만 일부 복제본이 아직 할당되지 않음 (클러스터가 완전히 작동함)

- Red - some data is not available for whatever reason (cluster is partially functional)
- Red - 어떤 이유로든 일부 데이터를 사용할 수 없음 (클러스터가 부분적으로 기능함)

**Note**: When a cluster is red, it will continue to serve search requests from the available shards but you will likely need to fix it ASAP since there are unassigned shards.  
**Note**: 클러스터가 빨간색이면 사용 가능한 샤드의 검색 요청을 계속 처리하지만 할당되지 않은 샤드가 있으므로 최대한 빨리 수정해야 한다.  

Also from the above response, we can see a total of 1 node and that we have 0 shards since we have no data in it yet. Note that since we are using the default cluster name (elasticsearch) and since Elasticsearch uses unicast network discovery by default to find other nodes on the same machine, it is possible that you could accidentally start up more than one node on your computer and have them all join a single cluster. In this scenario, you may see more than 1 node in the above response.  
또한 위의 응답으로부터 총 1개의 노드를 볼 수 있으며, 아직 데이터가 없기 때문에 0개의 shard를 가지고 있다. 기본 클러스터 이름 (elasticsearch)을 사용하고 있으며, Elasticsearch는 기본적으로 유니캐스트 네트워크 검색을 사용하여 동일한 시스템에서 다른 노드를 찾기 때문에 실수로 컴퓨터에서 둘 이상의 노드를 시작하여 모두 단일 클러스터에 가입시킬 수 있다는 점에 유의하십시오. 이 시나리오에서는 위의 응답에 2개 이상의 노드를 볼 수 있다.

We can also get a list of nodes in our cluster as follows:  
또한 다음과 같이 클러스터에 있는 노드 목록을 얻을 수 있다.

```bash
GET /_cat/nodes?v
```

And the response:
그리고 응답:

```bash
ip        heap.percent ram.percent cpu load_1m load_5m load_15m node.role master name
127.0.0.1           10           5   5    4.46                        mdi      *      PB2SGZY
```

Here, we can see our one node named "PB2SGZY", which is the single node that is currently in our cluster.  
여기서는 현재 클러스터에 있는 단일 노드인 "PB2SGZY"라는 이름의 노드를 볼 수 있다.

#### [1-3-2) List All Indices](https://www.elastic.co/guide/en/elasticsearch/reference/7.x/getting-started-list-indices.html)

Now let’s take a peek at our indices:  
이제 우리의 index를 살펴보자.

```bash
GET /_cat/indices?v
```

And the response:  
그리고 응답:

```bash
health status index uuid pri rep docs.count docs.deleted store.size pri.store.size
```

Which simply means we have no indices yet in the cluster.  
이것 간단히 말해서 우리가 아직 클러스터에 index를 가지고 있지 않다는 것을 의미한다.

#### [1-3-3) Create an Index](https://www.elastic.co/guide/en/elasticsearch/reference/7.x/getting-started-create-index.html)

Now let’s create an index named "customer" and then list all the indexes again:  
이제 "customer"이라는 index를 생성한 후 모든 index를 다시 나열해 봅시다.

```bash
PUT /customer?pretty
GET /_cat/indices?v
```

The first command creates the index named "customer" using the PUT verb. We simply append pretty to the end of the call to tell it to pretty-print the JSON response (if any).  
첫 번째 명령은 PUT 동사를 사용하여 "customer"이라는 index를 만든다. JSON 응답(있는 경우)을 예쁘게 출력하기 위해 호출 끝 부분에 pretty를 추가하기만 하면 된다.

And the response:  
그리고 응답:

```bash
health status index    uuid                   pri rep docs.count docs.deleted store.size pri.store.size
yellow open   customer 95SQ4TSUT7mWBT7VNHH67A   1   1          0            0       260b           260b
```

The results of the second command tells us that we now have one index named customer and it has one primary shard and one replica (the defaults) and it contains zero documents in it.  
두 번째 명령의 결과에 따르면 우리는 이제 고객이라는 하나의 index를 가지고 있고 그것은 하나의 기본 shard와 하나의 replica (기본값) 가지고 있으며 그 안에 0개의 문서를 포함하고 있다.

You might also notice that the customer index has a yellow health tagged to it. Recall from our previous discussion that yellow means that some replicas are not (yet) allocated. The reason this happens for this index is because Elasticsearch by default created one replica for this index. Since we only have one node running at the moment, that one replica cannot yet be allocated (for high availability) until a later point in time when another node joins the cluster. Once that replica gets allocated onto a second node, the health status for this index will turn to green.  
당신은 또한 고객 index에 노란색 health 태그가 붙어 있는 것을 발견할 수 있다. 이전 토론에서 노란색은 일부 복제본이 할당되지 않았다는 것을 의미한다는 것을 상기하십시오. 이 index에 대해 이러한 현상이 발생하는 이유는 기본적으로 Elasticsearch가 이 index에 대한 하나의 replica를 생성했기 때문이다. 현재 하나의 노드만 실행되고 있기 때문에, 다른 노드가 클러스터에 합류하는 나중의 시점까지 하나의 replica를 아직 할당(고가용성)할 수 없다. 복제본이 두 번째 노드에 할당되면 이 index의 상태가 녹색으로 변한다.

#### [1-3-4) Index and Query a Document](https://www.elastic.co/guide/en/elasticsearch/reference/7.x/getting-started-query-document.html)

Let’s now put something into our customer index. We’ll index a simple customer document into the customer index, with an ID of 1 as follows:  
이제 고객 index에 뭔가를 넣자. 다음과 같이 ID가 1인 간단한 고객 document를 고객 index에 index할 것이다.

```bash
PUT /customer/_doc/1?pretty
{
  "name": "John Doe"
}
```

And the response:  
그리고 응답:

```bash
{
  "_index" : "customer",
  "_type" : "_doc",
  "_id" : "1",
  "_version" : 1,
  "result" : "created",
  "_shards" : {
    "total" : 2,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 0,
  "_primary_term" : 1
}
```

From the above, we can see that a new customer document was successfully created inside the customer index. The document also has an internal id of 1 which we specified at index time.  
위에서, 우리는 새로운 고객 docuemnt가 고객 index 안에서 성공적으로 작성되었음을 알 수 있다. 이 document는 또한 index 시간에 지정한 내부 ID 1을 가지고 있다.

It is important to note that Elasticsearch does not require you to explicitly create an index first before you can index documents into it. In the previous example, Elasticsearch will automatically create the customer index if it didn’t already exist beforehand.    
Elasticsearch는 document를 index하기 전에 명시적으로 index를 생성할 것을 요구하지 않는다는 점에 유의해야 한다. 앞의 예에서, Elasticsearch는 사전에 존재하지 않은 customer index를 자동으로 생성한다.

Let’s now retrieve that document that we just indexed:  
이제 방금 index한 문서를 검색해 봅시다.

```bash
GET /customer/_doc/1?pretty
```

And the response:  
그리고 응답:

```bash
{
  "_index" : "customer",
  "_type" : "_doc",
  "_id" : "1",
  "_version" : 1,
  "_seq_no" : 25,
  "_primary_term" : 1,
  "found" : true,
  "_source" : { "name": "John Doe" }
}
```

Nothing out of the ordinary here other than a field, `found`, stating that we found a document with the requested ID 1 and another field, `_source`, which returns the full JSON document that we indexed from the previous step.  
요청한 ID인 1을 가진 document를 발견했다는 것을 나타내는 `found` 필드와 이전 단계에서 index한 전체 JSON document를 반환하는 `_source` 필드를 외에 특이한 것은 없다.

#### [1-3-5) Delete an Index](https://www.elastic.co/guide/en/elasticsearch/reference/7.x/getting-started-delete-index.html)

Now let’s delete the index that we just created and then list all the indexes again:  
이제 방금 생성한 index를 삭제한 후 모든 index를 다시 나열해 봅시다.

```bash
DELETE /customer?pretty
GET /_cat/indices?v
```

And the response:  
그리고 응답:

```bash
health status index uuid pri rep docs.count docs.deleted store.size pri.store.size
```

Which means that the index was deleted successfully and we are now back to where we started with nothing in our cluster.  
이는 index가 성공적으로 삭제되었고 이제 클러스터에서 아무것도 없이 시작했던 때으로 되돌아갔다는 것을 의미한다.

Before we move on, let’s take a closer look again at some of the API commands that we have learned so far:  
다음으로 넘어가기 전에 지금까지 학습한 API 명령 중 몇 가지를 다시 한 번 자세히 살펴봅시다.

```bash
PUT /customer
PUT /customer/_doc/1
{
  "name": "John Doe"
}
GET /customer/_doc/1
DELETE /customer
```

If we study the above commands carefully, we can actually see a pattern of how we access data in Elasticsearch. That pattern can be summarized as follows:  
위의 명령어를 주의 깊게 연구하면, 실제로 우리가 Elasticsearch에서 데이터에 접근하는 패턴을 볼 수 있다. 이 패턴은 다음과 같이 요약할 수 있다.

```bash
<HTTP Verb> /<Index>/<Endpoint>/<ID>
```

This REST access pattern is so pervasive throughout all the API commands that if you can simply remember it, you will have a good head start at mastering Elasticsearch.  
이 REST 액세스 패턴은 모든 API 명령어 전체에 매우 널리 퍼져 있어서, 단순히 기억할 수 있다면, Elasticsearch를 숙달하는 데 있어서 좋은 출발점이 될 것이다.

### [1-4. Modifying Your Data](https://www.elastic.co/guide/en/elasticsearch/reference/7.x/getting-started-modify-data.html)

Elasticsearch provides data manipulation and search capabilities in near real time. By default, you can expect a one second delay (refresh interval) from the time you index/update/delete your data until the time that it appears in your search results. This is an important distinction from other platforms like SQL wherein data is immediately available after a transaction is completed.  
Elasticsearch는 거의 실시간으로 데이터 조작 및 검색 기능을 제공한다. 기본적으로 데이터를 index/updeate/delete 할 때부터 검색 결과에 나타날 때까지 1초 지연(새로 고침 간격)을 예상할 수 있다. 이는 트랜잭션이 완료된 후 즉시 데이터를 사용할 수 있는 SQL과 같은 다른 플랫폼과의 중요한 차이점이다.


**Indexing/Replacing Documents**

We’ve previously seen how we can index a single document. Let’s recall that command again:  
우리는 이전에 단일 documnet를 index할 수 있는 방법을 본 적이 있다. 그 명령을 다시 한 번 생각해 봅시다.

```bash
PUT /customer/_doc/1?pretty
{
  "name": "John Doe"
}
```

Again, the above will index the specified document into the customer index, with the ID of 1. If we then executed the above command again with a different (or same) document, Elasticsearch will replace (i.e. reindex) a new document on top of the existing one with the ID of 1:  
다시, 위 명령어는 customer index에 지정된 document를 ID를 1로 index할 것이다. 그런 다음 위의 명령을 다른(또는 동일한) document로 다시 실행하면, Elasticsearch는 기존 document 위에 새 document를 ID 1로 대체(다시 index)할 것이다.

```bash
PUT /customer/_doc/1?pretty
{
  "name": "Jane Doe"
}
```

The above changes the name of the document with the ID of 1 from "John Doe" to "Jane Doe". If, on the other hand, we use a different ID, a new document will be indexed and the existing document(s) already in the index remains untouched.  
위 명령어에서는 ID가 1인 document의 이름을 "John Doe"에서 "Jane Doe"로 변경한다. 반면에 다른 ID를 사용하면 새 document가 index되고 이미 index에 있는 기존 document는 그대로 유지된다.

```bash
PUT /customer/_doc/2?pretty
{
  "name": "Jane Doe"
}
```

The above indexes a new document with an ID of 2.  
위 명령어 에서는 ID가 2인 새 document가 index된다.

When indexing, the ID part is optional. If not specified, Elasticsearch will generate a random ID and then use it to index the document. The actual ID Elasticsearch generates (or whatever we specified explicitly in the previous examples) is returned as part of the index API call.  
indexing할 때 ID 부분은 선택사항이다. 지정되지 않은 경우, Elasticsearch는 랜덤 ID를 생성한 다음 이를 사용하여 document를 index한다. 실제 Elasticsearch가 생성하는 ID(또는 앞의 예에서 명시적으로 지정한 ID)는 index API 호출의 일부로 반환된다.

This example shows how to index a document without an explicit ID:  
이 예에서는 명시적 ID 없이 document를 index하는 방법을 보여 준다.

```bash
POST /customer/_doc?pretty
{
  "name": "Jane Doe"
}
```

Note that in the above case, we are using the POST verb instead of PUT since we didn’t specify an ID.  
위의 경우 특정 ID를 지정하지 않았기 때문에 PUT 대신 POST 동사를 사용하고 있다는 점에 유의한다.

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