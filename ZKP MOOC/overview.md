## SNARK란?
어떤 주장(state)이 사실이라 할 수 있는 간결한(succint) 증명으로<br/>
proof가 짧고, 검증이 빨리 되어야한다

<br/><br/>

## arithmetic circuit
DH키교환에서 설명한 finite field 내에서 선언되며

<img width="240" alt="image" src="https://github.com/dik654/Zero_knowledge/assets/33992354/39b41fe6-84e3-4beb-b75a-b81cbb432528">

위와 같이 다항식을 나타내는 DAG 그래프 회로를 뜻한다


이러한 회로의 예로 MAC, ECDSA verify 회로가 있을 수 있다
MAC 회로는 hash와 메세지를 입력을 받아서 -> hash - SHA256(메세지) = 0 이면 verify되는 회로이고, <br/>
ECDSA 회로는 공개키와 메세지, 서명을 받아서 서명이 공개키로 verify되면 0을 리턴하는 회로이다

<br/><br/>

## structured와 unstructured circuit
unstructured circuit = 어떤 문제를 해결하기 위해 특정 구조나 패턴을 따르지 않는 회로(유연하지만 해석이 어려움)<br/>
structured circuit = 반복되는 구조와 패턴을 갖는 계층적 구조의 회로로, 특정 계산 문제를 위해 설계된다 

<br/><br/>

## NARK(Non-interactive ARgument of Knowledge)
<img width="822" alt="image" src="https://github.com/dik654/Zero_knowledge/assets/33992354/f44b7e79-14cf-4e26-b6ce-174045da395c">

위 이미지처럼 NARK에서는 S, P, V가 각각 역할 분담을 한다<br/>
S는 proving parameters, verification parameters를 생성하고<br/>
P는 증명을 생성하고<br/> 
V는 증명을 검증한다
succint preprocessing NARK는 witness sublinear하고 회로가 sublinear해야하고
strongly succint하려면 회로가 log로 증가한다

![image](https://github.com/dik654/Zero_knowledge/assets/33992354/49609c85-8a77-469f-96c6-e490fe0f84f2)

## setup의 종류
회로마다 setup을 설정하는 경우 <br/>
**회로마다 다르고, prover가 알 수 없는** 비밀값(r)을 이용하여 setup을 진행한다 S(C; r)
만약 prover가 r값을 알게 되는 경우, 잘못된 statement에 대해서 proof를 생성할 수 있게된다

한번의 setup으로 여러 회로에 대해 setup을 하는 경우 <br/>
init setup과 index setup 두 개로 나눠서 setup을 한다<br/>
init setup은 비밀값(r)을 이용하여 global parameter를 얻는 과정으로, 단 한번만 진행하고<br/>
그 이후로는 index setup을 이용하여 proving parameters, verification parameters를 생성하는데,<br/>
index setup는 인수로 init setup에서 생성한 global parameter와 회로를 사용하여 r값은 한번, 회로만 돌려가면서 setup이 가능해진다<br/>

마지막으로 setup없이 진행하는 경우가 있다

![image](https://github.com/dik654/Zero_knowledge/assets/33992354/f9b677a5-1e77-4253-a828-352318f3555a)


## knowledge soundness의 정의
증명해야할 목표 : verify에 성공했다면 prover가 C(x,w) = 0을 만족시키는 witness를 알고있다
증명 과정은 아래와 같다

![image](https://github.com/dik654/Zero_knowledge/assets/33992354/46e23b43-c049-4dd7-84cd-87d480509dee)

## SNARK 생성 절차
![image](https://github.com/dik654/Zero_knowledge/assets/33992354/97d8192f-73a4-400e-9965-45de466b7f72)

commitment의 과정과 특성은 아래와 같다
commitment의 예로는 HMAC이 있다

![image](https://github.com/dik654/Zero_knowledge/assets/33992354/d68db58c-5207-4031-b6e0-63a52bf33eeb)

## 함수 commitment
![image](https://github.com/dik654/Zero_knowledge/assets/33992354/e86843ba-dc7d-4936-a9bb-d4056431f972)

![image](https://github.com/dik654/Zero_knowledge/assets/33992354/f9a469bc-f761-4839-8c31-80016137b489)

![image](https://github.com/dik654/Zero_knowledge/assets/33992354/1db1f3b2-9378-4d37-8726-e71152e13b50)
다항식이 0인지 확인하는 테스트
![image](https://github.com/dik654/Zero_knowledge/assets/33992354/2199e52e-cb3e-4440-b5fe-9697c488e116)

두 커밋된 다항식이 동일한지 확인하는 테스트
![image](https://github.com/dik654/Zero_knowledge/assets/33992354/b69e9cb3-5f01-4153-808a-7249e90b984c)

### public coin interactive protocol 
- verifier가 랜덤값을 제공하면 prover가 증명을 보내주는 형식
Fiat-Shamir transform :
- public coin interactive protocol을 비대화식으로 바꾸기 위해서<br/>
  어떤 랜덤값 생성함수를 만들고 그 함수의 초기값을 verifier가 설정하게하여<br/>
  prover가 증명을 생성하기 전에 스스로 랜덤값을 생성하도록 하는 방식

## IOP
verify를 하는데 있어서 많은 리소스가 들기 때문에 prover와 verifier 사이에 대신 계산을 해주는 oracle이라는 중간자를 두는 방식
