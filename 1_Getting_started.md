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