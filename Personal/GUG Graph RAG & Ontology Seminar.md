---   

# 1. Opening

지식 그래프, 온톨로지 라는 단어들이 심심치 않게 보이고 있다. (feat. Youtuber 빅데이터닥터)
온톨로지 : 각각의 속성들을 컴퓨터스럽게 표현해놓은것

Data Lineage와 Ontology를 통한 Data 관리와 활용 -> 사내 데이터를 잘 써보자.
If KaKao -> Meta Chunk쪽 지식그래프 활용

# 2. 온톨로지 구축 및 평가
발표자 : Naver 전희선님

1. **관련 개념** 
	- 온톨로지 : 세상에 대해 사람들이 보고, 느끼고, 생각하는 것 -> 컴퓨터가 이해할 수 있는 방식으로 정의하는 것 
	- knowledge를 graph로 표현, 각 entity사이의 relationship을 연결하여 표현
2. **기존의 온톨로지 구축방식**
	1. 수동 구축 : 도메인 전문가
	2. 말뭉치 (text corpora) 이용
	3. Wikipedia 분류체계 이용 (Wikipedica Category Network, WCN)
3. **분류체계 생성**
	1. 상위 분류에서 하위분류로의 방향성을 나타내는 방향 비순환 그래프 (DAG)
	2. 그래프 가지치기 (pruning)
		1. 한 정점에 도달할 수 있는 다른 정점의 비율
4. **다중 상위분류**
	1. 기존의 분류체계는 1개의 상위분류만을 지님
5. **온톨로지 평가 방식 및 지표**
	1. Golden Standard
	2. Data Driven
	3. Aplication / Task based
	4. User based
	5. Structure-based
6. **Structured-based**
	1. Schema Metrics
		1. 분류 체계의 구조 특성을 담은 지표
			1. Attribute Richness (AR) : Class . 당평균 property(attributte) 수
				1. class에 해당하는 property가 얼마나 다양한지 나타내는 지표
			2. Inheritance Richness(IR) : class당 평ㄱ균 subclass 수
			3. Class Richness (CR) : instance가 존재하는 class 비율
			4. Average Population (P) : class당 평균 instance 수
			5. Importance (IMP) : 전체 instance 대비 해당 class에 속하는 instance 비율
			6. Relationship Richness (RR) : 해당 class의 property 중 실제 데이터가 존재하는 property 비율
	2. Instance Metrics
		1. Instance 분포 정보를 담은 지표
	3. Class Metrics
		1. Class별 특성을 담은 지표
7. **Class Granularity**
	1. 기존 metric은 class 세분화에 대한 평가 기준이 어려움
	2. DP (Distinct Property) : 해당 class에만 정의되어 있는 property 수
	3. IDPP : 각 class별 distinct property가 사용되는 비율
	4. IDPPA : 각 class별 IDPP의 평균
	5. Class Granularity : 모든 class에 대한 IDPPA 평균 (값이 클수록 class별 고유 속성을 잘 보유하고 있다고 판단)
8. **요약 및 결론**
	1. 향후 계층 구조 깊이 등을 고려한 지표 개발필요
9. **QnA**
	1. 문서의 분류체계에 관점에서 분류기준을 어떻게 세울 수 있는가?
		=> 관계를 나타내는 일정 패턴을 기준으로 세우는것이 좋지 않은가
	2. 동일한 단어지만 문맥적으로 다른 의미를 가진 경우에는 어떤 metric이 어울리나?
		=> 해당 단어를 instance로 취급하여 볼 수 있어 보이니 instance metric이 좋다고 생각함

# 3. 온톨로지와 GraphRAG
발표자 : 비트나인 곽상환님

1. **생성형 AI**
	1. ai의 5대 핵심 기능 : 자동화, 인식, 예측, 소통, 생성
2. **그래프 RAG**
	1. RAG는 본질적으로 context와 vector similarity에 의존할 수 밖에 없으니 그 연결관계를 더 명확히 하면 어떨까?
	2. SPO 추출 후 Cypher query로 변환
	3. Apache AGE -> Postgres 기반의 그래프 DB 확장기능
	4. Multi-Layer KG (데이터의 메타 정보에 대한 그래프와 지식 그래프간 multi-layer를 참조)
	5. Graph Metric (중심성, Centrality 이나 클러스터링 clustering , 퍼콜레이션 모델등의 메트릭을 활용)
3. **QnA**
	1. 지식 그래프를 어떻게 구축하냐?
		1. llm을 활용한 spo 추출
		2. 전통적인 spo 추출
		3. vector chunk를 바탕으로 spo 추출 (이게 가장 성능이 좋았음. 가설은 전통적 spo 추출)
	2. 파일 종류에 따른 GraphRAG vs RAG vs LLM acc 측정
		1. 사람을 갈아서 수행함 ㅋ
		2. 