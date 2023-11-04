## SNARK란?
어떤 주장(state)이 사실이라 할 수 있는 간결한(succint) 증명으로<br/>
proof가 짧고, 검증이 빨리 되어야한다

## arithmetic circuit
DH키교환에서 설명한 finite field 내에서 선언되며

<img width="240" alt="image" src="https://github.com/dik654/Zero_knowledge/assets/33992354/39b41fe6-84e3-4beb-b75a-b81cbb432528">

위와 같이 다항식을 나타내는 DAG 그래프 회로를 뜻한다

이러한 회로의 예로 MAC, ECDSA verify 회로가 있을 수 있다
MAC 회로는 hash와 메세지를 입력을 받아서 -> hash - SHA256(메세지) = 0 이면 verify되는 회로이고, <br/>
ECDSA 회로는 공개키와 메세지, 서명을 받아서 서명이 공개키로 verify되면 0을 리턴하는 회로이다

## structured와 unstructured circuit
unstructured circuit = 어떤 문제를 해결하기 위해 특정 구조나 패턴을 따르지 않는 회로(유연하지만 해석이 어려움)<br/>
structured circuit = 반복되는 구조와 패턴을 갖는 계층적 구조의 회로로, 특정 계산 문제를 위해 설계된다 

## NARK(Non-interactive ARgument of Knowledge)
<img width="822" alt="image" src="https://github.com/dik654/Zero_knowledge/assets/33992354/f44b7e79-14cf-4e26-b6ce-174045da395c">

위 이미지처럼 NARK에서는 S, P, V가 각각 역할 분담을 한다<br/>
S는 proving parameters, verification parameters를 생성하고<br/>
P는 증명을 생성하고<br/> 
V는 증명을 검증한다
