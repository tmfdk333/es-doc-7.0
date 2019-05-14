# [ElasticSearch Cookbook - 3/e](https://www.aladin.co.kr/shop/wproduct.aspx?ISBN=K312534137&start=pnaver_02)

## 1장. 시작하기 
1. 노드와 클러스터 이해 
2. 노드 서비스 이해 
3. 데이터 관리 
4. 클러스터, 레플리케이션, 샤딩의 이해 
5. 일래스틱서치와 통신 
6. HTTP 프로토콜 사용 
7. 네이티브 프로토콜 사용 

## 2장. 다운로드와 설정 
1. 일래스틱서치 다운로드 및 설치 
2. 네트워킹 설정 
3. 노드 설정 
4. 리눅스 시스템을 위한 설정 
5. 다양한 노드 타입 설정 
6. 클라이언트 노드 설정 
7. 수집 노드 설정 
8. 일래스틱서치에 플러그인 설치 
9. 플러그인 수동 설치 
10. 플러그인 제거 
11. 로깅 설정 변경 
12. 도커를 통한 노드 설정 

## 3장. 매핑 관리 
1. 명시적 매핑 생성 사용 
2. 기본 타입 매핑 
3. 매핑 배열 
4. 준비 
5. 객체 매핑 
6. 도큐먼트 매핑 
7. 도큐먼트 매핑에서 동적 템플릿 사용 
8. 중첩 객체 관리 
9. 자식 도큐먼트 관리 
10. 다중 매핑으로 필드 추가 
11. GeoPoint 필드 매핑 
12. GeoShape 필드 매핑 
13. IP 필드 매핑 
14. 첨부 필드 매핑 
15. 매핑에 메타데이터 추가 
16. 다양한 분석기 지정 
17. 자동 완성 필드 매핑 

## 4장. 기본 작업 
1. 색인 생성 
2. 색인 삭제 
3. 색인 열고 닫기 
4. 색인에 매핑 입력 
5. 매핑 조회 
6. 색인 재생성 
7. 색인 새로 고침 
8. 색인 플러시 
9. 색인 강제 병합 
10. 색인 축소 
11. 색인과 타입 존재 여부 확인 
12. 색인 설정 관리 
13. 색인 앨리어스 사용 
14. 색인 롤오버 
15. 도큐먼트 색인 
16. 도큐먼트 조회 
17. 도큐먼트 삭제 
18. 도큐먼트 변경 
19. 원자성 작업 속도 향상(벌크 작업) 
20. GET 작업 속도 향상(다중 GET) 

## 5장. 검색 
1. 검색 실행 
2. 정렬 
3. 하일라이팅 
4. 스크롤 쿼리 실행 
5. search_after 기능 사용 
6. 결과의 inner hits 반환 
7. 올바른 쿼리 제안 
8. 일치한 결과 카운트 
9. explain 쿼리 
10. 쿼리 프로파일링 
11. 쿼리에 의한 삭제 
12. 쿼리에 의한 변경 
13. 전체 도큐먼트 일치 
14. 불리언 쿼리 사용 

## 6장. 텍스트 및 수치형 퀴리 
1. term 쿼리 사용 
2. terms 쿼리 사용 
3. prefix 쿼리 사용 
4. wildcard 쿼리 사용 
5. regexp 쿼리 사용 
6. span 쿼리 사용 
7. match 쿼리 사용 
8. query_string 쿼리 사용 
9. simple_query_string 쿼리 사용 
10. range 쿼리 사용 
11. common terms 쿼리 
12. ID 쿼리 사용 
13. function score 쿼리 사용 
14. exists 쿼리 사용 
15. template 쿼리 사용 

> ## ~~7장. 관계 및 지오 퀴리~~
> 1. ~~has_child 쿼리 사용~~
> 2. ~~has_parent 쿼리 사용~~
> 3. ~~nested 쿼리 사용~~
> 4. ~~geo_bounding_box 쿼리 사용~~
> 5. ~~geo_polygon 쿼리 사용~~
> 6. ~~geo_distance 쿼리 사용~~
> 7. ~~geo_distance_range 쿼리 사용~~

## 8장. 집계 
1. 집계 실행 
2. stats 집계 실행 
3. terms 집계 실행 
4. significant_terms 집계 실행 
5. range 집계 실행 
6. histogram 집계 실행 
7. date_histogram 집계 실행 
8. filter 집계 실행 
9. filters 집계 실행 
10. global 집계 실행 
11. geo_distance 집계 실행 
12. children 집계 실행 
13. nested 집계 실행 
14. top_hits 집계 실행 
15. matrix_stats 집계 실행 
16. geo_bounds 집계 실행 
17. geo_centroid 집계 실행 

> ## ~~9장. 스크립팅~~
> 1. ~~페인리스 스크립팅~~
> 2. ~~추가 스크립트 플러그인 설치~~
> 3. ~~스크립트 관리~~
> 4. ~~스크립트를 사용한 데이터 정렬~~
> 5. ~~스크립팅으로 반환 필드 계산~~
> 6. ~~스크립팅을 통한 검색 필터링~~
> 7. ~~집계에 스크립팅 사용~~
> 8. ~~스크립트를 사용한 도큐먼트 업데이트~~
> 9. ~~스크립트로 재색인~~

## 10장. 클러스터와 노드 관리
1. API를 통한 클러스터 헬스 제어
2. API를 통한 클러스터 상태 제어
3. API를 통해 노드 정보 얻기
4. API를 통해 노드 통계 가져오기
5. 태스크 관리 API 사용
6. 핫 스레드 API
7. 샤드 할당 관리
8. 세그먼트 API로 세그먼트 모니터링
9. 캐시 정리

> ## ~~11장. 백업 및 복구~~
> 1. ~~저장소 관리~~
> 2. ~~스냅샷 실행~~
> 3. ~~스냅샷 복구~~
> 4. ~~백업용 NFS 공유 설정~~
> 5. ~~원격 클러스터에서 재색인~~

> ## ~~12장. 사용자 인터페이스~~
> 1. ~~세레브로 설치 및 사용~~
> 2. ~~키바나와 엑스팩 설치~~
> 3. ~~키바나 대시보드 관리~~
> 4. ~~키바나로 모니터링~~
> 5. ~~키바나 개발 콘솔 사용~~
> 6. ~~키바나로 데이터 시각화~~
> 7. ~~키바나 플러그인 설치~~
> 8. ~~키바나로 그래프 생성~~

> ## ~~13장. 인제스트~~
> 1. ~~파이프라인 정의~~
> 2. ~~인제스트 파이프라인 넣기~~
> 3. ~~인제스트 파이프라인 가져오기~~
> 4. ~~인제스트 파이프라인 삭제~~
> 5. ~~인제스트 파이프라인 시뮬레이션~~
> 6. ~~내장 프로세서~~
> 7. ~~그락 프로세서~~
> 8. ~~인제스트 첨부 플러그인 사용~~
> 9. ~~인제스트 GeoIP 플러그인 사용~~

> ## ~~14장. 자바 통합~~
> 1. ~~표준 자바 HTTP 클라언트 생성~~
> 2. ~~HTTP 일래스틱서치 클라이언트 생성~~
> 3. ~~네이티브 클라이언트 생성~~
> 4. ~~네이티브 클라이언트로 색인 관리~~
> 5. ~~매핑 관리~~
> 6. ~~문서 관리~~
> 7. ~~벌크 작업 관리~~
> 8. ~~쿼리 작성~~
> 9. ~~표준 검색 실행~~
> 10. ~~집계와 함께 검색 실행~~
> 11. ~~스크롤 검색 실행~~

> ## ~~15장. 스칼라 통합~~ 
> 1. ~~스칼라로 클라이언트 생성~~
> 2. ~~색인 관리~~
> 3. ~~매핑 관리~~
> 4. ~~도큐먼트 관리~~
> 5. ~~표준 검색 실행~~
> 6. ~~집계와 함께 검색 실행~~

> ## ~~16장. 파이썬 통합~~
> 1. ~~클라이언트 생성~~
> 2. ~~색인 관리~~
> 3. ~~매핑을 포함한 mappings 관리~~
> 4. ~~도큐먼트 관리~~
> 5. ~~표준 검색 실행~~
> 6. ~~집계와 함께 검색 실행~~

> ## ~~17장. 플러그인 개발~~
> 1. ~~플러그인 만들기~~
> 2. ~~분석기 플러그인 만들기~~ 
> 3. ~~REST 플러그인 만들기~~
> 4. ~~클러스터 액션 만들기~~
> 5. ~~인제스트 플러그인 만들기~~

> ## ~~18장. 빅데이터 통합~~ 
> 1. ~~아파치 스파크 설치~~
> 2. ~~아파치 스파크를 통한 데이터 색인~~ 
> 3. ~~아파치 스파크를 통한 메타데이터 색인~~ 
> 4. ~~아파치 스파크로 데이터 읽기~~
> 5. ~~SparkSQL을 사용해 데이터 읽기~~ 
> 6. ~~아파치 피그로 데이터 색인~~