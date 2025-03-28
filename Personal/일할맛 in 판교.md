-- -

## 세미나 1부 : From RAG to Graph RAG

GUG Organizer 정이태 연사님

**GraphRAG**
- Hard Prompting
- Soft Prompting

**History of GraphRAG**
- GraphRAG (MS) (Hard Prompting)
- G-Retriever - Path Filtering (Hard Prompting & Soft Prompting)
- HybridRAG (Hard Prompting)
- Graph RAG Autotuning (Hard Prompting)
- G-Retrieval Module with PyG (Hard Prompting)
- LightRAG Keyword & Entity Extraction (Hard Prompting)
- GraphRAG Dynamic Community Selection (Hard Prompting)
- GraphRAG - LazyGraphRAG (Hard Prompting)
- GFM-RAG - Foundation Module (Soft Prompting)
- PathRAG - Path Filtering (Hard Prompting)


**어떻게 Graph를 만드는가?**
- Graph를 왜 사용해야 하는가? 데이터에 도메인의 성격을 입혀야 함.

- Multi-hop reasoning
- Common Knowledge

**GraphRAG** 
- ( Public Domain ) 
	- Prompt Engineering 
	- Unstructure data
- ( Enterprise Domain ) 
	- Entity Resolution
	- GDBMS
	- Document Relationship
	- Re-ranking
	- Graph Schema
- ( Public Domain )
	- Graph CI/CD
	- Ontology
	- Evaluation Data

**표를 그래프로 표현하는 방식**
- 메타 데이터를 통합이 필요
	- 다수의 DB를 통합해야하는 케이스가 발생 => Scalability & Heterogeneous graph 데이터 관리를 위해 적절한 GDBMS 필요.
	- 각 node의 property를 전부 활용하자 (keyword, vector)
	- table의 column, row별 메타데이터를 활용해야함.
	- Prompt 추상화 수준에 따라 답변 품질 또한 달라진다.
		- Task Routing
			- e.g. general, specific
		- Prompt Hooking
			- Select of prompt

**그래프를 조회하는 방식**
- Text2Cypher (https://graphrag.com)
	- Prompt Engineering
		- LLM이 나의 Schema를 인지하지 못함.
		- Graph-CoT Prompt
		- Langchain의 graphqachain
	- Multi-Hop Search
		- Subgraph Extraction, Scalability
			- Single-Hop 답변들만 가져올거였으면, vector여도 충분했을 텐데..?
		- hop을 거듭할수록 조회 cost가 배로 증가한다.
		

**그래프를 평가하는 방식**
- 그래프를 평가하는 기준
	- Vector RAG랑 비교하는 방법?
	- 평가 데이터셋은 어떻게 만들지?
		- Graph chain-of-thought : Augmenting large language models by reasoning on graphs
		- COSMO : a large-scale e-commerce common sense knowledge generation and serving system at Amazon
	- Reranker 기준은 어떻게 만들지?
		- meta data 관리 오픈소스 툴
		- opik RAG CI/CD 툴
		- llm orchestration : hydra

**개인 Insight**
- 최초 기획 및 정의가 가장 중요하다.
- 결국 도메인의 암묵지를 전달(추출, 발견)받는것이 중요하다.
- Prompt Engineering이 구석구석 들어가고 품질을 받춰줘야 한다.
- Text2SQL 
	- SQL Logs를 메타 데이터로 활용하자, pinterest의 text2sql medium과 github(query book)을 참조하자.
- 대부분의 방식이 llm을 활용한 작업으로 수행됨
- Graph 구조가 용이한 데이터가 아니면 추천하지 않는다.
- Multi-Turn Retrieval Iterative 방식도 좋음!

**Q&A**
Q : entity/resolution 추출을 위한 prompt engineering부분에서 기법적인 연사님만의 팁이 있는지?
A : 학계가 아닌 산업계에서 작성한 prompt 템플릿을 마주한 도메인 및 상황에 맞게 적용해보고 유효하면 그대로 차용하는 편



## 세미나 2부 : Multi-modal RAG 트렌드 살펴보기

김용담 연사

MultiModal RAG가 핫해진 이유?
- MultiModal Agent가 떠올랐기 때문

여러 modality를 가지는 데이터를 multi modal 데이터라고 함.
Vision Language Model
- CLIP, DALLE, Stable Diffusion, ImageBind, ColPali
- 서로 다른 유형과 modality의 데이터가 의미가비슷하다면 유사한 embedding space에 위치하길 바란다.

RAG의 목적은 "유저의 질문과 연관된 정보를 잘 찾는것"이 핵심!
- 이것을 잘하려면 무슨 방법이 있을까?
	- 유저에게 책임을 던지는 밥법
		- 질문을 잘 줘라.
			- e.g. 요즘 reasoning model의 경우 애매한 질문인 경우 해당 질문이 맞는지 처리

Multi Modal Embedding
- 가장 많이 사용하는 것이 Contrastive Learning

**Trends**
1. **Shared Embedding Space**
	1. UniVL-DR
		1. query, text, image triple-set을 학습
		2. Verbalize : Image에 대한 captioning
		3. Contrastive Learning
		4. OpenCLIP
2. **Domain-Specified**
	1. FactMM-RAG
		1. F1RadGraph (Factual Report Pairs Mining)
3. **Multi-document Understanding**
	1. M3DocRAG
			1. Many document의 경우 image로 처리하는게 더 좋다.
		1. M3DocVQA Benchmark
4. **Benchmark dataset**
	1. UniIR
		1. MBeir
5. **Approximate Nearest Neighbor Search**
	1. KNN의 퀄리티는 embedding model이 중요함.
	2. text domain에서 HNSW는 성능 굿
		1. Big ANN Competition
		2. roar graph


**개인 Insight**
- Dataset 제작이 필수적으로 동반된다.
- Billion Size의 RAG에서는 Dense Retrieval을 할 수가 없다. 거의 Sparse Retrieval을 선호하는 편
	- 대규모 트래픽이 있는 경우에는 Single-Turn은 무조건 한다.
	- 검색엔진은 Multi-hop을 상정하지 않을 수 있다.
	- 

**Q&A**
Q : Multimodal embedding model을 학습할 때 Contrastive Learning을 수행하는데, 데이터셋도 구축하여 사용해야하는데, 일반적으로 hard negative sample을 어떠한 방식으로 만드시나요?
A : 휴리스틱하게 데이터셋을 구축한다. Hard Negative Sample의 Hard한 정도의 범주가 많이 확장된다고 이해하면 될 것 같다.