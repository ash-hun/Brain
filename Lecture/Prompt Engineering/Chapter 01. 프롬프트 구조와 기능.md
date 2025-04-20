-- -
# 1.  User Intent 파악을 위한 단서들

단서가 될 수 있는 정보들?
- 프롬프트
- 사용자 로그 데이터
- 고객의 소리 (VoC : Voice of Customer)

프롬프트로만 intent를 파악해보자.

*[Paper] : Understanding User's Dissatisfaction with ChatGPT Responses: Types, Tesolving Tactics, and the Effect of Knowledge Level*

user는 프롬프트 작성에 최소한의 노력을 기울인다. 작성에 전략이 없거나 프롬프트를 재사용한다는 결론.
- 프롬프트 재사용
- 의도 구체화
- 오류 식별 및 수정
- 작업 적응
- 없음

*[Book] 변화의 상수 : 분화하는 사회, "Think First" not "Just Do it"*

# 2. 프롬프트 구조

프롬프트 작문 유형
- 명령/청유형
- 역할 지정
- 상황극형
- 설명형
- 간단형

### 명령/청유형 프롬프트
- 업장에 산학 실습을 가는데 실습개요와 목표를 알려줘
- 우아한 거짓말 독후감 써줘
- 봉은사역에서 메가박스 가는 길 말해
- RTX4090 가장 싸게 사는 방법 알려줘봐
- 저는 이전에는 없던 창업 아이디어를 찾고 있는데, 어떤 분야를 추천주시겠어요?

```
중요한 회의 일정을 변경해야해. [청유형으로 작성]
팀원들에게 보내는 정중하고 간결한 이메일을 작성해.

다음 사항을 반드시 포함해. [커스텀 내용을 넘버링하여 작성]
1. 회의 일정 변경 사유 : 부득이한 개인 사정으로 연차
2. 변경된 새로운 회의 일정 알림 : 8/7일 오후 2시에서 8/12일 오후 2시, 3A 회의룸으로 변경
3. 회의 참여를 독려하는 문구 추가
4. 회의 준비사항
5. 마무리 인사말
```

### 역할지정 프롬프트
- 너는 고객서비스 상담사처럼 행동해. 고객의 감정에 최대한 공감할 수 있는 표현을 사용해. 아래 [단계]의 순서에 맞게 답변을 생성해줘.
- 너는 헤르만 헤세야. 헤르만 헤세의 작품을 통해 인간의 감정과 사회적 이슈를 알고 싶은 독자를 위해 상세하게 설명해줘.

```
당신은 신생 친환경 스타트업의 마케팅 책임자입니다.
Z세대를 타겟으로 한 소셜 미디어 마케팅 전략 5가지를 제안해주세요.
<인플루언서 협업>을 소재로 해주세요.

- 각 전략의 구체적인 설명
- 전략이 효과적인 이유
- 실행방법
- 기대되는 결과
- 성공 여부를 평가하는 방법

```

### 상황극형
- 너는 지금 곰하고 같이 있어. 곰을 따라하는 게 너의 역할이야. "크앙", "그르렁", "Grrr...", 울음소리로만 대화해야해.
- 우리는 지금 심리상담 센터에 같이 있어. 너는 인공지능이야. 말 시작할 때 "흐음"으로 항상 시작하면서 심리상담을 해주길 바래.

```
지금 우리는 중소기업 의료기기판매 회사의 면접장에 있어.
후보자가 높은 연봉을 요구해. 나는 이 후보자 마음에 들어.
연봉 협상을 해야하는데, 대화를 시뮬레이션해보면 좋겠어.
어떤 시뮬레이션을 하면 좋을까?
```

### 설명형
- 2023년 알뜰교통카드 신청 안내
- 대중교통비 최대 30%까지 절감할 수 있는 교통카드
```
클라우드 컴퓨팅의 개념과 장점을 A4 이내의 분량으로 작성해줘.
보고서를 읽을 대상은 기술 개념을 이해하기 어려워하는 경영진이야.
작성 내용은 아래의 지시를 따라줘.

- 중심 내용 : 클라우드 컴퓨팅의 정의, 기본 원리, 주요 장점,
- 문장 스타일 : 경영진이 이해할 수 있도록하는 쉬운 예시나 비유를 사용
- 핵심 : 클라우드 컴퓨팅 도입시 기대할 수 있는 비즈니스 효과

[참고 텍스트]를 사용해서 내용을 상세하게 써줘.
클라우드 컴퓨팅 도입 시, 초기 자본 지출을 줄이고, 운영 효율성을 높이며, 비즈니스 확장 시 신속하게 대응할 수 있습니다. 또한 직원들이 어디서나 업무를 볼 수 있어 업무 효율성이 증가하고, 최신 기술을 빠르게 도입할 수 있는 장점이 있습니다.

[참고 텍스트]
blah blah
```

### 간단형
- 강남맛집
- 비오는 날 카톡 멘트

```

```

### 공통적인 특징

- Task Description (작업 설명)
- Specific Instructions (구체적인 지침)
- Content Elements (내용 요소)
- Audience and Role Specification (청중 및 역할 지침)
- Language and Style Guidelines (언어 및 스타일 지침)
- Format or Structure Guidelines (형식 또는 구조 지침)
- Word or Character Limits (단어 또는 문자 제한)


# 3. 사용자 AI 상호작용 매커니즘 분석

생성형 AI가 혁신적인 까닭은 **Interface**에 있다.

Turn : 대화에서 한 사람이 말을 시작하고 끝내는 한 단위의 발화를 의미
Structure : 대화의 전반적인 조직 방식을 의미. 턴의 교환 규칙, 순서, 주제 전화, 대화 참여자 간의 상호작용 패턴

언어분석 3가지 요소
- 문화적 맥락 (언어 외적 요소)
- 상황적 맥락 (언어 외적 요소)
- 텍스트 (언어 요소)

대화 분석 4가지 기준
- Turn
	- 싱글 턴
	- 멀티 턴
- Action
	- 정보 검색 유형
	- 다른 행위 유형
- Structure
	- 선호 구조
	- 비선호 구조
- Stance
	- 감정적 태도
	- 비감정적 태도

```
1.    ((ring))
2.    Nancy : H'llo:?
3.    Hyla: Hi:,
4.    Nancy: Hi:::
5.    Hyla: How are. yuhh.=
6.    Nancy: =Fi:ne how're you.
```

Rule
1. Opening (lines 1-2)
2. Greetings and Identification (lines 3-4)
3. Initial enquiries (lines 5-6)

사람의 대화는 서로 말을 하고 이것은 상호간의 이해 덕분에 가능한 것.

### Turn

Turn : Systematic patterns in the conversations w/h AI
- Single Turn : human의 대화보다 더 systematic하다.
- Multi Turn : 같은 topic으로 single turn을 여러번 덧 붙인 것

Single Turn과 Multi Turn을 구분하는 prompt 예제
```
Your task is to determine whether the given text represents a single turn or multiple turns.

- Single turn : involves only one the same topic.
- Multiple turns : involves two or more conversational topics.

Text : {  }
Your Answer : {  }
```

