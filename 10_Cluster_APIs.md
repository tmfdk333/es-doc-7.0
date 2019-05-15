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