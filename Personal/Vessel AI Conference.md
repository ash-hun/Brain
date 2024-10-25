---
aliases:
---

---  

Document Processing Tagging & Extraction

How to make the better AI Agent System
- Data splitting
- Embedding Model
- Reranking
- Planning - Action
- Tooling (Function calling)
- Memory


Agent
- AI 시스템이 주어진 목표를 달성하기 위 LLM을 기반으로 스스로 판단하고, 추론하고, 작업을 수행하는 것.

o1-preview
- 각 단계를 분리하여 구조화 (Reasoning & Planning)

Agent Component
- Planning
	- subtask화, self-reflection
- Memory
- Action
- Tool Use

지향점은 다수의 agent system의 모음이 될 것이고 각 agent system사이 상호소통이 시너지를 낼 것. => Multi-Agent System

Agentic Workflow

AGI : Compound AI System

General AI Agent System은 수백개의 AI agent로 이루어진다.

Q&A : Short Term Memory & Long Term Memory 의 구성 및 관리?
-> Application / Use case에 따라 달라진다.


AWS Serverless Lambda : Auto-Scaling

보안의 의한 LM 선택 (API 사용 x)
미용 도메인 데이터의 부재로 인한 파인튜닝의 어려움

강남언니 LLM 학습 법 (엥?)
- Format-Prompting
- Few Shot
- Post-Processing

과거의 경량화는 edgeAI에서만 올리기 위한 기술이었다..!
현재는 LLM을 보편적으로 사용하기 위해 꼭 필요하다!

Perform Metrics
- Throughput
- Time to First Token (TTFT)
- Time per Output Token (TPOT)


Average Prompt Length : 2048 token
Average Output Length : 128 token

tpot : 20 m/s

와 같은 전제조건을 가지고 engineering

fishonchips.ai

한국어 RAG 평가와 최적화

1. AutoRAG에서 주장하는 RAG의 각 단계에 대한 최적화 -> Advanced RAG에 있는 각 단계마다 평가기준을 따로 두는건지? 가령 decomposition의 경우 task를 sub-task로 쪼개는 것에 대한 auto-rag만의 기준이 존재하는지가 궁금
2. Chunking에 대한 평가방식이 궁금합니다.
3. 평가셋을 제작하는 과정에서 Retriever gt를 선택하는 기준이 따로 존재하는지 궁금합니다.