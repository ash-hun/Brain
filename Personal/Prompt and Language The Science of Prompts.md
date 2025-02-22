----  

**Agenda : 언어학적인 프롬프트의 접근**

강연자 : 강수진 박사님

- 언어학적 이론을 접목한 프롬프트는 뛰어나다!
- Evaluating User Satisfactoin in LLMs : Linguistic Analysis of Actual User Conversation 
(2023.05. ~ 2024.12.)


생각해보자! 언어학이 앞으로 가져올 세상에 얼만큼 중요하다 생각하는가?

Linguistics : 언어학을 과학적으로 공부하는 학문

Linguistic와 Prompt와의 관계
- 단어 의미를 못찾으면 의미 모호성을 줄여야 함
- 맥락을 잃거나 못찾으면 인간의 인지 구조와 개념 체계를 이해해야 함
- 문장 레벨 이상의의미 해석을 못하면 담화와 대화 구조를 이해해야 함

언어는 다수의 layer로 구성되어있음
-> 형태소, 단어, 구, 문장

- **Syntax (문장의 통사론)** : The set of rules that govern the structure and arrangement of words in sentences.
		- 문장이 어떻게 구성될까? (e.g. 주어, 술어, 목적어 등)
		- 생성문법과 구문 규칙파싱
		- 구조적 해석
	
		- Generation Grammar : 모든 언어는 근간을 이루는 규칙을 가진다. 
		  (e.g. X-bar Theory, Chomsky(=1970) and Jackendoff(=1977))
		  
		  - A Cute Cat에서 가장 중요한 것은 무엇일까?
			- Cat이 핵심이 되는 오브젝트
		- 모든 문장은 핵(core)이 있고 이를 중심으로 왼쪽 또는 오른쪽으로 확장될 수 있다. 보통 명사가 핵을 차지함.
	
		? 차이점은 무엇일까요 ?
			- The boy likes the girl
			- The girl likes the boy
			- 철수가 희를 좋아한다
			- 희를 철수가 좋아한다
			- 좋아한다 철수가 희를
		- 즉, 어순이 중요한 언어가 있고, 그렇지 않은 언어가 있다.
	- Syntax Tree : 단어들 간의 수직적 위계 관계가 존재한다. 문장 구조가 지니는 계층 표상 방법
			- 언어의 모호성을 표현해주기 위해서!
			- [젊은 [남자와 여자]]가 방에 있다.
		- 인간이 언어 능력(competence)을 선천적으로 타고남. 
		- 언어학은 바로 이 언어 능력을 규명하는 것을 목표로 삼아야 함.
	- Recursive Rule : 동일한 규칙이 반복되어 복잡한 구조를 형성하는 것. LLM 프롬프트 설계 시 이러한 규칙들을 명시하거나 암시하여 모델이 문장 구조를 올바르게 이해하고 생성하도록 유도한다. 인간 언어의 특성을 논의하면서, 반복성
		- 명사구의 무한 반복
			- 나는 철수와 희와 수와 명철과 숙자와 ... 놀았다.
		- 동사구의 무한 반복
			- 그는 걷고 먹고 자고 뛰고 걷고 먹고 자고 쉬고 ...
		- 절의 무한 반복
			- 부사절 : 철수가 희가 수가 예쁘다고 생각한다고 말했다.
		- 관형절의 무한 반복
		- 구구조규칙 : A => B C
			- The boy likes the girl.
				- NP => D N
			- **Hidden Meanings : Testing AI on language comprehension tasks reveals insensitivity to underlying meaning**
				- 일부 문법적 오류(e.g. 주어-동사 불일치, 비교문 오류, 동사 누락 등)를 처리하지 못함.
				- 낮은 빈도로 등장하는 어려운 문법 구조에서 성능이 저하됨.
				- semantic anomalies (의미적 이상 현상) 문장에서 논리적 모순을 제대로 인식하지 못함.
			- X-bar 이론을 바탕으로 문장의 핵을 중심으로 번역해줘.
				- 번역에는 의역과 직역이 존재하고, 사람이 자연스럽다고 느끼는 것은 의역에 가깝다.
- **Semantics (의미학)** : The study of meaning in language, focusing on how words, phrases, and sentences convey meaning.
	- 이름(object) : 사과
	- 문장(function) : 사과는 ___
	- Metaphysics (=형이상학)
		- 존재하는 것들은 어떤 방식으로 존재하는가? => Object
		- 사물과 개념은 어떤 관계인가? => Function
			- 사과는 물리적으로 존재하는가? (변하지 않고)
			- 빨간색은 사과가 가진 속성인가? (변한다)
		- 의미를 규정하는 방식이 가장 중요함
			- 의미란 무엇인가?
				- Frege's Semantics/metaphysics
				- 의미 구성 (Copositional Semantics):
				  단어, 구, 문장이 어떻게 결합되어 전체적인 의미를 형성하는지 설명
					- 전체의 의미는 그 구성요소들의 의미와 결합 방식에 의해 결정된다 (원리적 구성성)
					- 진리값(truth-value)
						- *John* is named *John*. : object는 단 하나도 없음.
				- Semantic Relations : 의미적 관계
					- 동의어 : 의미가 유사한 단어들
					- 반의어 : 서로 반대되는 의미의 단어들
					- 다의어 & 중의성 : 하나의 단어가 여러 의미를 가질 때 발생하는 문제
					- 텍스트 해석 시, 단어의 선택과 문맥에 따라 의미가 크게 달라질 수 있음. LLM은 통계적 패턴을 바탕으로 단어의 다의성 문제에 직면
				
					- 빈도수가 많은 단어가 그 문서에서 중요한 단어인가? 정답은 No!
						- I went to the bank
							- 나는 은행에 갔었다.
							- 나는 강가에 갔었다.
						- She saw the man with the telescope.
							- 그녀는 망원경으로 남자를 봤다.
							- 그녀는 망원경을 가지고 있는 남자를 봤다.
						- The chicken is ready to eat.
							- 닭이 먹을 준비가 됐어.
							- (내가) 닭을 먹을 준비가 됐어.
					- Reference Theory : 어떤 단어나 표현이 실제 세계에서 특정한 대상(참조 대상)을 직접 지시
						- 러셀 : 고유 명사는 그 자체로 특정한 대상을 지시한다.
						- 프레게 : 의미와 지시를 구분하며, 단어의 의미는 단순히 대상이 아니라 개념적 내용도 포함할 수 있다.
							- 그는 천재야
								- 그 : 대명사
								- 천재 : 속성
					- Deixis
						- Personal Deixis
							- 그, 그녀
						- Temporal Deixis
							- 지역적 사투리(e.g. 거시기), 공간을 지칭
						- Spatial Deixis
							- 그사람만 이해하는 표현
						- Discourse Deixis
							- 담화 내에서만 이해하는 표현 (e.g. As I Said before)
				- Conceptual Semantics (=개념적 의미론)
					- 인지구조의 기본 요소
						- 감각 경험과 지각
							- 인간은 주변세계를 감각 기관을 통해 경험
							- 감각 기관
								- 시각, 청각, 촉각 등
							- 동적 경험
								- 문화, 개인 학습 경험
						- 프로토타입(=Prototype)
							- 인간은 범주를 구성할 때 전형적인 예(=프로토타입)를 기준으로 판단(비둘기=평화)
						- 스키마와 프레임(=Schema & Frame)
							- 개인이 경험한 정보를 조직화 (병원=가운, 의사, 흰색)
						- 개념적 은유(=Conceptual Metaphor)
							- 시간은 돈이다.
				- 은유와 metonymy : Lakoff, G. & Johnson, M. (1980). Metaphors We Live By.
					- 은유 : 한 개념 영역에서 ㅏ른 개념 영역으로 의미가 전이되는 방식으로, "시간은 돈이다 "와 같은 표현
					- 환유 : 어떤 개념을 그와 밀접하게 관련된 다른 개념으로 대체하는 것으로, "백악관이 발표했다."에서 백악관은 미국을 의미
					- Personal Calendar 만들기
						- 데이터가 완벽해야 동작할 수 있으나 사용자는 그렇게 입력하지 않음.
						- Idea : 상황인지를 기본 베이스로 디폴트로 수행
					- 중의성 문제
						- 명확한 용어 사용
					- 문맥 부족
						- 구조적 명료성 제공, 프롬프트 구조화
						- 배경 및 컨텍스트 명시, 맥락 추가
					- 참조 오류
						- 샷 사용
				- **RAGged Edges: The Double-Edged Sword of Retrieval-Augmented Chatbots**
				- RAG는 Semantic loss가 굉장히 심함.
					- 기존 데이터가 가지는 tone & manner가 모두 사라져버림
 - Pragmatics (화용론) : Pragmatics is the study of how context influences how we interpret and make meaning of communication. It is often described as the study of "language in use".
	 - 언어는 Lower Context와 Higher Context가 있음.
		 - Higher Context : 이거 저거 그거는 그거이거다.
		 - Lower Context : 영어같은 언어들
		 - 한국어는 Higher Context
		- Examples
			- metaphor
			- irony
			- sarcasm
			- delxis
			- euphemisms
			- jokes and humor
			- silence / mis en scence
			- hyperbote
			- tautologies
		- The social situation
		- The relationship between the speakers
		- the cultural context
		- the situational context
		- the way the word and said
	- Personal Space
		- 화자와 청자의 상황
			- 대화가 이루어지는 시간, 장소, 사회적 관계 등이 의미해석에 영향을 미침
		- 암시와 암묵적 의미
			- 명시적으로 언급되지 않은 정보(예: 암시, 전제, 배경지식)를 통해 의도된 의미를 도출함
	- Grice's Cooperative Principle (협력의 원칙) -> Human Like한 conversation이 가능하다.
		- Maxim of Quality : 진실된 정보를 제공할 것
		- Maxim of Quantity : 적당한 양을 말할것
		- Maxim of Relation : 관련된 정보만 말할 것
		- Maxim of Manner : 매너를 지켜 말할 것
	- Speech Act Theory : 발화행위이론, 발화는 단순 정보 전달이 아니라, 실제로 요청, 명령, 질문, 약속 등 수행 행위(illocutionry act)를 포함함.
		- Locutionary act : The process of saying itself
		- Illocutionary act : The intention of saying smth
		- Perlocutionary act : The effect of saying smth

		- Representative or Assertive
		- Directive
		- Commisive
		- Expressive
		- Declarative

		- **A Prompt Pattern Catalog to enhance prompt Engineering with ChatGPT**
			- e.g. "From now on"
		- **Response Generation with Context-Aware Prompt Learning**
		- **Principled Instructions Are All You Need for Questioning LLaMA-1/2, GPT-3.5/4**
			- 발화 행위의 명시 (Explicit Speech Act Specification)
	- Politeness and Conversational Norms : Politeness is the word we use to talk about a speaker's intention to threaten or save fae of a hearer.
	- FTA (Brown & Levinson's, 1978)
		- **Should we respect LLMs? A Cross-Lingual Study on the Influence of Prompt Politeness on LLM Performance**
			- 특정 모델에서는 공손성이 성능에 더 큰 영향을 미친다.
	- LLMs and Culture
		- **CDEval : A Benchmark for Measuring the Cultural Dimensions of Large Language Models**
	- **KoBBQ : Korean Bias Benchmark for Question Answering**
	- **Does Cross-Cultural Alignment Change the Commonsense Morality of Language Models?**
	- **Do Multilingual Large Language Models Mitigate Stereotype Bias?**
	- Persona prompting : 대부분의 모델에게 AI라는 페르소나가 주어지면 비교적 성능이 좋지 않다는 것
	- **Cultural sensitivity and biases**


	**QnA**
		1. 꼭 영어로만 prompt를 작성해야 하나요?
			1. 무조건 그런것은 아니나 보편적으로 영어로 쓰고, 사용하는 llm이 학습되지 않은 것 같은 단어라면 영어와 한글을 같이 병기해준다.
			2. 한국어를 사용하는 사람들의 특징을 명시적으로 덧붙여서 prompt를 작성해준다.
		2. safe guard를 만드는 경험
			1. stop words를 정말 많이 만든다.
			2. 100% 성능은 불가능, 보편적으로 80% 이상 나오면 성공
		3. prompt를 위한 prompt (=meta prompt)를 만들 수 있는가?
			1. 가장 중요한 건 user intention
		4. CoT없이 프롬프트 정확도를 높이는 방법?
		5. Tool Calling에 대한 프롬프트 변형법
		6. Embodied Action을 이해할 수 있나?
		7. 