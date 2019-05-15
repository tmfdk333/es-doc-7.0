## [[10] Cluster APIs](https://www.elastic.co/guide/en/elasticsearch/reference/7.x/cluster.html)

**Node specification**  
Some cluster-level APIs may operate on a subset of the nodes which can be specified with node filters. For example, the [Task Management](https://www.elastic.co/guide/en/elasticsearch/reference/7.x/tasks.html), [Nodes Stats](https://www.elastic.co/guide/en/elasticsearch/reference/7.x/cluster-nodes-stats.html), and [Nodes Info](https://www.elastic.co/guide/en/elasticsearch/reference/7.x/cluster-nodes-info.html) APIs can all report results from a filtered set of nodes rather than from all nodes.  
일부 클러스터 레벨 API는 노드 필터로 지정할 수 있는 노드의 하위 집합에서 작동할 수 있다. 예를 들어 태스크 관리, 노드 통계 및 노드 정보 API는 모두 모든 노드가 아닌 필터링된 노드 집합에서 결과를 보고할 수 있다.

Node filters are written as a comma-separated list of individual filters, each of which adds or removes nodes from the chosen subset. Each filter can be one of the following:  
노드 필터는 각각 선택된 하위 집합에서 노드를 추가하거나 제거하는 개별 필터의 쉼표로 구분된 목록으로 작성된다. 각 필터는 다음 중 하나가 될 수 있다.
  
- `_all`, to add all nodes to the subset.
- `_all`, 모든 노드를 서브셋에 추가.

+ `_local`, to add the local node to the subset.
+ `_local`, 로컬 노드를 서브셋에 추가.

- `_master`, to add the currently-elected master node to the subset.
- `_master`, 현재 선택된 마스터 노드를 서브셋에 추가.

+ a node id or name, to add this node to the subset.
+ 노드 ID 또는 이름, 이 노드를 서브셋에 추가.

- an IP address or hostname, to add all matching nodes to the subset.
- IP 주소 또는 호스트 이름, 일치하는 모든 노드를 서브셋에 추가.

+ a pattern, using `*` wildcards, which adds all nodes to the subset whose name, address or hostname matches the pattern.
+ `*` 와일드카드를 사용한 패턴이 이름, 주소, 호스트 이름과 일치하는 모든 노드를 서브셋에 추가.

- `master:true`, `data:true`, `ingest:true` or `coordinating_only:true`, which respectively add to the subset all master-eligible nodes, all data nodes, all ingest nodes, and all coordinating-only nodes.
- `master:true`, `data:true`, `ingest:true` or `coordinating_only:true`, 모든 마스터 적격 노드, 데이터 노드, 수집 노드, 조정 전용 노드를 각각 서브셋에 추가.

+ `master:false`, `data:false`, `ingest:false` or `coordinating_only:false`, which respectively remove from the subset all master-eligible nodes, all data nodes, all ingest nodes, and all coordinating-only nodes.
+ `master:false`, `data:false`, `ingest:false` or `coordinating_only:false`, 모든 마스터 적격 노드, 데이터 노드, 수집 노드, 조정 전용 노드를 각각 서브셋에서 제거.

- a pair of patterns, using `*` wildcards, of the form `attrname:attrvalue`, which adds to the subset all nodes with a custom node attribute whose name and value match the respective patterns. Custom node attributes are configured by setting properties in the configuration file of the form `node.attr.attrname: attrvalue`.
- `*` 와일드카드를 사용한 `attrname:attrvalue` 형식의 패턴, 커스텀 노드 속성이 이름과 값의 패턴에 일치하는 모든 노드를 서브셋에 추가. 커스텀 노드 속성은 구성 파일에 `attrname:attrvalue` 특성을 설정하여 구성된다. 

> **Note** ❓  
> node filters run in the order in which they are given, which is important if using filters that remove nodes from the set. For example `_all,master:false` means all the nodes except the master-eligible ones, but `master:false,_all` means the same as `_all` because the `_all` filter runs after the `master:false` filter.  
> 노드 필터는 주어진 순서대로 실행되며, 세트에서 노드를 제거하는 필터를 사용할 경우 중요하다. 예를 들면, `_all,master:false`는 마스터 적격 노드를 제외한 모든 노드를 의미하지만, `master:false,_all`은 `_all`과 같다. `_all` 필터는 `master:false` 뒤에 실행되기 때문이다.

> **Note** ❓  
> if no filters are given, the default is to select all nodes. However, if any filters are given then they run starting with an empty chosen subset. This means that filters such as `master:false` which remove nodes from the chosen subset are only useful if they come after some other filters. When used on its own, `master:false` selects no nodes.  
> 필터가 없는 경우, 기본값은 모든 노드를 선택하는 것이다. 그러나, 만약 필터가 주어지면, 그것들은 비어있는 선택된 서브셋으로 시작한다. 이 의미는 선택된 서브셋에서 노드를 제거하는 `master:false` 같은 필터들은 다른 필터를 사용하는 경우에만 유용하다. 자체적으로 사용될 경우 `master : false`는 노드를 선택하지 않는다.


Here are some examples of the use of node filters with the [Nodes Info](https://www.elastic.co/guide/en/elasticsearch/reference/7.x/cluster-nodes-info.html) APIs.  
다음은 노드 정보 API를 사용한 노드 필터 사용에 대한 몇 가지 예입니다.

```bash
# If no filters are given, the default is to select all nodes
GET /_nodes
# Explicitly select all nodes
GET /_nodes/_all
# Select just the local node
GET /_nodes/_local
# Select the elected master node
GET /_nodes/_master
# Select nodes by name, which can include wildcards
GET /_nodes/node_name_goes_here
GET /_nodes/node_name_goes_*
# Select nodes by address, which can include wildcards
GET /_nodes/10.0.0.3,10.0.0.4
GET /_nodes/10.0.0.*
# Select nodes by role
GET /_nodes/_all,master:false
GET /_nodes/data:true,ingest:true
GET /_nodes/coordinating_only:true
# Select nodes by custom attribute (e.g. with something like `node.attr.rack: 2` in the configuration file)
GET /_nodes/rack:2
GET /_nodes/ra*:2
GET /_nodes/ra*:2*
```

### [10-1. Cluster Health](https://www.elastic.co/guide/en/elasticsearch/reference/7.x/cluster-health.html)

The cluster health API allows to get a very simple status on the health of the cluster. For example, on a quiet single node cluster with a single index with one shard and one replica, this:  
클러스터 상태 API를 사용하면 클러스터 상태에 대해 매우 간단한 상태를 얻을 수 있다. 예를 들어, 하나의 샤드 및 하나의 복제본이 있는 단일 인덱스가 있는 조용한 단일 노드 클러스터에서,

```bash
GET _cluster/health
```

Returns this:  
반환 결과:

```bash
{
  "cluster_name" : "testcluster",
  "status" : "yellow",
  "timed_out" : false,
  "number_of_nodes" : 1,
  "number_of_data_nodes" : 1,
  "active_primary_shards" : 1,
  "active_shards" : 1,
  "relocating_shards" : 0,
  "initializing_shards" : 0,
  "unassigned_shards" : 1,
  "delayed_unassigned_shards": 0,
  "number_of_pending_tasks" : 0,
  "number_of_in_flight_fetch": 0,
  "task_max_waiting_in_queue_millis": 0,
  "active_shards_percent_as_number": 50.0
}
```

The API can also be executed against one or more indices to get just the specified indices health:  
또한 API는 지정된 인덱스 상태만 얻기 위해 하나 이상의 인덱스에 대해 실행될 수 있다.

```bash
GET /_cluster/health/test1,test2
```

The cluster health status is: `green`, `yellow` or `red`. On the shard level, a `red` status indicates that the specific shard is not allocated in the cluster, `yellow` means that the primary shard is allocated but replicas are not, and `green` means that all shards are allocated. The index level status is controlled by the worst shard status. The cluster status is controlled by the worst index status.  
클러스터 상태는 녹색, 노란색 또는 빨간색입니다. 샤드 수준에서 빨간색 상태는 특정 샤드가 클러스터에 할당되지 않았음을 나타내며, 노란색은 기본 샤드가 할당되었지만 복제본이 할당되지 않았음을 의미하며, 녹색은 모든 샤드가 할당되었음을 의미한다. index 레벨 상태는 최악의 샤드 상태에 의해 제어된다. 클러스터 상태는 최악의 index 상태로 제어된다.

One of the main benefits of the API is the ability to wait until the cluster reaches a certain high water-mark health level. For example, the following will wait for 50 seconds for the cluster to reach the `yellow` level (if it reaches the `green` or `yellow` status before 50 seconds elapse, it will return at that point):  
API의 주요 이점 중 하나는 클러스터가 특정 높은 워터마 표시 상태 수준에 도달할 때까지 기다릴 수 있는 기능이다. 예를 들어, 클러스터가 노란색 수준에 도달할 때까지 50초간 기다리십시오(50초가 경과하기 전에 녹색 또는 노란색 상태에 도달하면 해당 지점에 반환됨).

```bash
GET /_cluster/health?wait_for_status=yellow&timeout=50s
```

**Request Parameters**  
The cluster health API accepts the following request parameters:
클러스터 상태 API는 다음과 같은 요청 매개 변수를 허용한다.


- `level`  
    - Can be one of `cluster`, `indices` or `shards`. Controls the details level of the health information returned. Defaults to `cluster`.
    - `cluster`, `indices` 또는 `shards`중 하나가 될 수 있다. 반환된 헬스 정보의 상세 레벨을 관리한다. 기본은 `cluster`이다.
+ `wait_for_status`
    + One of `green`, `yellow` or `red`. Will wait (until the timeout provided) until the status of the cluster changes to the one provided or better, i.e. `green` > `yellow` > `red`. By default, will not wait for any status.
    + `green`, `yellow` 또는 `red` 중 하나. 클러스터 상태가 제공된 클러스터 상태로 변경되거나 더 나아질 때까지(예. green > yellow > red) 기다릴 것이다(제공된 타임아웃까지). 기본적으로, 어떤 상태도 기다리지 않는다.
- `wait_for_no_relocating_shards`
    - A boolean value which controls whether to wait (until the timeout provided) for the cluster to have no shard relocations. Defaults to false, which means it will not wait for relocating shards.
    - 클러스터에 shard 재배치가 없을 때까지(제공된 타임아웃까지) 기다릴지 여부를 제어하는 부울 값. false로 기본 설정됨. 즉, shard를 재배치할 때까지 기다리지 않음.
+ `wait_for_no_initializing_shards`
    + A boolean value which controls whether to wait (until the timeout provided) for the cluster to have no shard initializations. Defaults to false, which means it will not wait for initializing shards.
    + 클러스터에 shard 초기화가 없을 때까지(제공된 타임아웃까지) 기다릴지 여부를 제어하는 부울 값. false로 기본 설정됨. 즉, shard를 초기할 때까지 기다리지 않음.
- `wait_for_active_shards`
    - A number controlling to how many active shards to wait for, `all` to wait for all shards in the cluster to be active, or `0` to not wait. Defaults to `0`.
    - 대기할 활성 샤드의 수를 제어하는 숫자, `all`은 클러스터의 모든 샤드가 활성화될 때까지 대기하거나 `0`은 대기하지 않음. 기본값은 0.
+ `wait_for_nodes`
    + The request waits until the specified number `N` of nodes is available. It also accepts `>=N`, `<=N`, `>N` and `<N`. Alternatively, it is possible to use `ge(N)`, `le(N)`, `gt(N)` and `lt(N)` notation.
    + 요청은 지정된 노드 수 N을 사용할 수 있을 때까지 대기한다. 또한 >=N, <=N, >N, <N>을 받아들인다. 또는 ge(N), l(N), gt(N) 및 lt(N) 표기법을 사용할 수 있다.
- `wait_for_events`
    - Can be one of `immediate`, `urgent`, `high`, `normal`, `low`, `languid`. Wait until all currently queued events with the given priority are processed.
    - `immadiate`, `urgent`, `high`, `normal`, `low`, `languid`중 하나일 수 있다. 지정된 우선 순위를 가진 현재 대기 중인 모든 이벤트가 처리될 때까지 기다리십시오.
+ `timeout`
    + A time based parameter controlling how long to wait if one of the wait_for_XXX are provided. Defaults to `30s`.
    + wait_for_XXX 중 하나가 제공된 경우 대기 시간을 제어하는 시간 기반 매개 변수. 기본값은 30초.
- `master_timeout`
    - A time based parameter controlling how long to wait if the master has not been discovered yet or disconnected. If not provided, uses the same value as `timeout`.
    - 마스터가 아직 검색되지 않았거나 연결이 끊어진 경우 대기하는 시간을 제어하는 시간 기반 매개 변수. 제공되지 않은 경우 시간 초과와 동일한 값을 사용.
+ `local`
    + If `true` returns the local node information and does not provide the state from master node. Default: `false`.
    + true인 경우 로컬 노드 정보를 반환하고 마스터 노드의 상태를 제공하지 않는다. 기본값: false.

The following is an example of getting the cluster health at the `shards` level:  
다음은 클러스터 상태를 'shards' 수준으로 얻은 예이다.

```bash
GET /_cluster/health/twitter?level=shards
```

### [10-2. Cluster State](https://www.elastic.co/guide/en/elasticsearch/reference/7.x/cluster-state.html)

The cluster state API allows access to metadata representing the state of the whole cluster. This includes information such as  
클러스터 상태 API를 사용하면 전체 클러스터의 상태를 나타내는 메타데이터에 액세스할 수 있다. 여기에는 다음과 같은 정보가 포함된다.

- the set of nodes in the cluster
- 클러스터의 노드 세트

+ all cluster-level settings
+ 모든 클러스터 수준 설정

- information about the indices in the cluster, including their mappings and settings
- 클러스터의 인덱스에 대한 정보(매핑 및 설정)

+ the locations of all the shards in the cluster
+ 클러스터에서 모든 shard의 위치

The response is an internal representation of the cluster state and its format may change from version to version. If possible, you should obtain any information from the cluster state using the other, more stable, [cluster APIs](https://www.elastic.co/guide/en/elasticsearch/reference/7.x/cluster.html).    
응답은 클러스터 상태에 대한 내부 표현이며 그 형식은 버전에서 버전으로 변경될 수 있다. 가능한 경우, 클러스터 API에서 더 안정적인 다른 것을 사용하여 클러스터의 상태에 대해 어떤 정보라도 얻어야 한다.

```bash
GET /_cluster/state
```

The response provides the cluster state itself, which can be filtered to only retrieve the parts of interest as described below.  
응답은 클러스터 상태 자체를 제공하며, 이 상태 자체는 아래에서 설명하는 대로 관심 부분만 검색하도록 필터링할 수 있다.

The cluster’s `cluster_uuid` is also returned as part of the top-level response, in addition to the `metadata` section. `📌Added in 6.4.0`  
클러스터의 `cluster_uuid`는 `metadata` 섹션 이외에도 응답의 최상위중 일부분으로 반환된다. 

> **Note**  
> While the cluster is still forming, it is possible for the `cluster_uuid` to be `_na_` as well as the cluster state’s version to be `-1`.  
> 클러스터가 계속 형성되는 동안, `cluster_uuid`는 `_na_`일 수 있으며 클러스터 상태의 버전은 `-1`이 될 수 있습니다.

By default, the cluster state request is routed to the master node, to ensure that the latest cluster state is returned. For debugging purposes, you can retrieve the cluster state local to a particular node by adding `local=true` to the query string.  
기본적으로 클러스터 상태 요청은 마스터 노드로 라우팅되어 최신 클러스터 상태가 반환되는지 확인합한다. 디버깅을 위해 쿼리 문자열에 `local=true`를 추가하여 특정 노드의 로컬 클러스터 상태를 검색 할 수 있습니다.

**Response Filters**  
The cluster state contains information about all the indices in the cluster, including their mappings, as well as templates and other metadata. This means it can sometimes be quite large. To avoid the need to process all this information you can request only the part of the cluster state that you need:  
클러스터 상태는 템플릿 및 기타 메타데이터뿐만 아니라 매핑을 포함하여 클러스터의 모든 인덱스에 대한 정보를 포함하고 있다. 이것은 때때로 꽤 클 수 있다는 것을 의미한다. 이 모든 정보를 처리할 필요가 없도록 필요한 클러스터 상태의 부분만 요청하십시오.

```bash
GET /_cluster/state/{metrics}
GET /_cluster/state/{metrics}/{indices}
```

- `{metrics}` is a comma-separated list of the following options.
- `{metrics}`는 다음 옵션의 쉼표로 구분된 목록이다.

+ `version`
     + Shows the cluster state version.
     + 클러스터 상태 버전을 표시.

- `master_node`
     - Shows the elected `master_node` part of the response
     - 응답의 선택된 `master_node` 부분을 표시
     
+ `nodes`
    + Shows the `nodes` part of the response
    + 응답의 `nodes` 부분을 표시.

- `routing_table`
    - Shows the `routing_table` part of the response. If you supply a comma separated list of indices, the returned output will only contain the routing table for these indices.
    - 응답의 `routing_table` 부분을 표시. 쉼표로 구분된 index 목록을 제공하는 경우 반환된 결과에는 이러한 index에 대한 라우팅 테이블만 포함된다.
    
+ `metadata`
    + Shows the `metadata` part of the response. If you supply a comma separated list of indices, the returned output will only contain metadata for these indices.
    + 응답의 `metadata` 부분을 표시. 쉼표로 구분된 index 목록을 제공하는 경우 반환된 결과에는 이러한 index 대한 메타데이터만 포함된다.

- `blocks`
    - Shows the `blocks` part of the response.
    - 응답의 `blocks` 부분을 표시.
    
+ `_all`
    + Shows all metrics.
    + 모든 metrics를 표시.
    
The following example returns only `metadata` and `routing_table` data for the `foo` and `bar` indices:  
다음 예제에서는 `foo` 및 `bar` index에 대한 메타데이터 및 라우팅_테이블 데이터만 반환한다.

```bash
GET /_cluster/state/metadata,routing_table/foo,bar
```

The next example returns everything for the `foo` and `bar` indices:  
다음 예제에서는 `foo` 및 `bar` index에 대한 모든 것을 반환한다.

```bash
GET /_cluster/state/_all/foo,bar
```

Finally, this example return only the `blocks` metadata:  
마지막으로, 이 예는 블록 메타데이터만 반환한다.

```bash
GET /_cluster/state/blocks
```

### [10-3. Cluster Stats](https://www.elastic.co/guide/en/elasticsearch/reference/7.x/cluster-stats.html)

The Cluster Stats API allows to retrieve statistics from a cluster wide perspective. The API returns basic index metrics (shard numbers, store size, memory usage) and information about the current nodes that form the cluster (number, roles, os, jvm versions, memory usage, cpu and installed plugins).  
Cluster Stats API를 사용하면 클러스터 넓은 관점에서 통계를 검색할 수 있다. API는 기본 index 메트릭(공유 번호, 저장소 크기, 메모리 사용량)과 클러스터를 구성하는 현재 node(숫자, 역할, os, jvm 버전, 메모리 사용량, cpu 및 설치된 플러그인)에 대한 정보를 반환한다.

```bash
GET /_cluster/stats?human&pretty
```

Will return, for example:  
예를 들어 다음과 같이 반환됨:  

```bash
{
   "_nodes" : {
      "total" : 1,
      "successful" : 1,
      "failed" : 0
   },
   "cluster_uuid": "YjAvIhsCQ9CbjWZb2qJw3Q",
   "cluster_name": "elasticsearch",
   "timestamp": 1459427693515,
   "status": "green",
   "indices": {
      "count": 1,
      "shards": {
         "total": 5,
         "primaries": 5,
         "replication": 0,
         "index": {
            "shards": {
               "min": 5,
               "max": 5,
               "avg": 5
            },
            "primaries": {
               "min": 5,
               "max": 5,
               "avg": 5
            },
            "replication": {
               "min": 0,
               "max": 0,
               "avg": 0
            }
         }
      },
      "docs": {
         "count": 10,
         "deleted": 0
      },
      "store": {
         "size": "16.2kb",
         "size_in_bytes": 16684
      },
      "fielddata": {
         "memory_size": "0b",
         "memory_size_in_bytes": 0,
         "evictions": 0
      },
      "query_cache": {
         "memory_size": "0b",
         "memory_size_in_bytes": 0,
         "total_count": 0,
         "hit_count": 0,
         "miss_count": 0,
         "cache_size": 0,
         "cache_count": 0,
         "evictions": 0
      },
      "completion": {
         "size": "0b",
         "size_in_bytes": 0
      },
      "segments": {
         "count": 4,
         "memory": "8.6kb",
         "memory_in_bytes": 8898,
         "terms_memory": "6.3kb",
         "terms_memory_in_bytes": 6522,
         "stored_fields_memory": "1.2kb",
         "stored_fields_memory_in_bytes": 1248,
         "term_vectors_memory": "0b",
         "term_vectors_memory_in_bytes": 0,
         "norms_memory": "384b",
         "norms_memory_in_bytes": 384,
         "points_memory" : "0b",
         "points_memory_in_bytes" : 0,
         "doc_values_memory": "744b",
         "doc_values_memory_in_bytes": 744,
         "index_writer_memory": "0b",
         "index_writer_memory_in_bytes": 0,
         "version_map_memory": "0b",
         "version_map_memory_in_bytes": 0,
         "fixed_bit_set": "0b",
         "fixed_bit_set_memory_in_bytes": 0,
         "max_unsafe_auto_id_timestamp" : -9223372036854775808,
         "file_sizes": {}
      }
   },
   "nodes": {
      "count": {
         "total": 1,
         "data": 1,
         "coordinating_only": 0,
         "master": 1,
         "ingest": 1
      },
      "versions": [
         "7.2.0"
      ],
      "os": {
         "available_processors": 8,
         "allocated_processors": 8,
         "names": [
            {
               "name": "Mac OS X",
               "count": 1
            }
         ],
         "pretty_names": [
            {
               "pretty_name": "Mac OS X",
               "count": 1
            }
         ],
         "mem" : {
            "total" : "16gb",
            "total_in_bytes" : 17179869184,
            "free" : "78.1mb",
            "free_in_bytes" : 81960960,
            "used" : "15.9gb",
            "used_in_bytes" : 17097908224,
            "free_percent" : 0,
            "used_percent" : 100
         }
      },
      "process": {
         "cpu": {
            "percent": 9
         },
         "open_file_descriptors": {
            "min": 268,
            "max": 268,
            "avg": 268
         }
      },
      "jvm": {
         "max_uptime": "13.7s",
         "max_uptime_in_millis": 13737,
         "versions": [
            {
               "version": "12",
               "vm_name": "OpenJDK 64-Bit Server VM",
               "vm_version": "12+33",
               "vm_vendor": "Oracle Corporation",
               "bundled_jdk": true,
               "using_bundled_jdk": true,
               "count": 1
            }
         ],
         "mem": {
            "heap_used": "57.5mb",
            "heap_used_in_bytes": 60312664,
            "heap_max": "989.8mb",
            "heap_max_in_bytes": 1037959168
         },
         "threads": 90
      },
      "fs": {
         "total": "200.6gb",
         "total_in_bytes": 215429193728,
         "free": "32.6gb",
         "free_in_bytes": 35064553472,
         "available": "32.4gb",
         "available_in_bytes": 34802409472
      },
      "plugins": [
        {
          "name": "analysis-icu",
          "version": "7.2.0",
          "description": "The ICU Analysis plugin integrates Lucene ICU module into elasticsearch, adding ICU relates analysis components.",
          "classname": "org.elasticsearch.plugin.analysis.icu.AnalysisICUPlugin",
          "has_native_controller": false
        },
        ...
      ],
      "network_types": {
        ...
      },
      "discovery_types": {
        ...
      },
      "packaging_types": [
        {
          ...
        }
      ]
   }
}
```

This API can be restricted to a subset of the nodes using [node filters](https://www.elastic.co/guide/en/elasticsearch/reference/7.x/cluster.html#cluster-nodes):  
이 API는 노드 필터를 사용하여 노드의 하위 집합으로 제한될 수 있다.  

```bash
GET /_cluster/stats/nodes/node1,node*,master:false
```

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