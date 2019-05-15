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