## sumcheck protocol
sumcheck protocol은 계산하기 어려운 g(b1, b2, ...)함수가 있고, verifier는 g 함수를 알고 있으며 prover가 g 함수를 알고 있는지 검사하는 과정이다.
함수 g의 내부의 인수 b들은 0 또는 1만을 받을 수 있는 상태하고 했을 때,<br/>
C1은 b1, b2, ...들의 모든 조합을 넣었을 때 g(0,0,...), g(0,1,...), g(1,0,...), g(1,1,...) 등 모든 경우의 결과들의 합을 나타낸다 

g 함수의 계산이 어렵다 가정했으므로 prover, verifier 모두에게 모든 경우의 수를 계산하는건 버겁다<br/>
따라서 같은 결과를 내지만 g 함수의 결과를 포함하고, 계산이 상대적으로 더 쉬운 multilinear extension를 찾아서<br/>
verifier는 특정한 b값들을 prover에게 제시하고 그 b값들을 가지고 ex) g~(0, 1, 0, 1, 1, ...) 이렇게 verifier가 준 한가지 경우에 대해서만 계산한다<br/>
verifier는 g 함수를 가지고 ex) g(0, 1, 0, 1, 1, ...) 에 대해 계산하고 (계산이 어렵지만 한가지 경우만 계산하므로 모든 경우를 계산하는 것보다 가볍다)<br/>
prover에게 받은 계산값과 verifier 자신이 계산한 결과를 비교하여<br/>
같으면 prover가 g 함수를 알고 있다고 판단한다

![image](https://github.com/dik654/Zero_knowledge/assets/33992354/33a9e9d9-9c05-4098-b27f-7fc3dedc4089)

<img width="1159" alt="image" src="https://github.com/dik654/Zero_knowledge/assets/33992354/469d4283-8883-445d-8f7d-8dbd605d19ee">

## KZG poly-commit scheme 

<img width="953" alt="image" src="https://github.com/dik654/Zero_knowledge/assets/33992354/47e20f24-a250-4fa0-995a-a00073592650">

