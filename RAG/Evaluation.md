-- --
# Retrieval Metrics
## Rank-Unware Metric

![[Pasted image 20250329170658.png]]
![[Pasted image 20250329170853.png]]
![[Pasted image 20250329170915.png]]
![[Pasted image 20250329171041.png]]
![[Pasted image 20250329171054.png]]
![[Pasted image 20250329171429.png]]

평가를 보는 순서
1. 일단 Recall First
	1. Retrieval에서 Recall은 accuracy와 동일하기 때문에 해당 값을 이용해서 Top-k를 정해준다.
	   일단, Recall이 어느정도 도출이 되지않으면 정답을 애초에 맞출수 없기 때문에 가장 먼저 고려하는 것.
	2. Recall이 어느정도 도출되면 
2. 



## Rank-Aware Metric
![[Pasted image 20250329172140.png]]
![[Pasted image 20250329172418.png]]
![[Pasted image 20250329172510.png]]
![[Pasted image 20250329172554.png]]
![[Pasted image 20250329172821.png]]
![[Pasted image 20250329172859.png]]
![[Pasted image 20250329173126.png]]
![[Pasted image 20250329173141.png]]
![[Pasted image 20250329173153.png]]
![[Pasted image 20250329173210.png]]
![[Pasted image 20250329173225.png]]
![[Pasted image 20250329173247.png]]


# Generation Metrics
- 기존의 LLM-as-a-judge가 널리 사용되지만 task별, domain별 evaluation metric은 천차만별이다.
![[Pasted image 20250329173742.png]]
