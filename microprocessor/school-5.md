이날은 웬일인지 간만에 눈이 덜 피로한 날이었다.
그래서 점심을 먹고도 마프 수업을 쌩쌩하게 들을 수 있을 것 같아서 기분이 좋았다.
어찌 됐든, 이날은 정보를 통신하는 각가지의 방법과 마이크로프로세서 개발환경을 구축하는 방법을 배우는 시간이었다. 

정보 통신하는 방법 1 > _______________________________________________________________________
-한 방향으로만 신호의 전송이 가능한 통신인 단방향 통신. -양방향으로 신호의 전송이 가능하지만, 상황에 따라 한 방향으로만 신호를 보낼 수가 있는 반이중 통신. -양방향 모두 동시에 신호를 전송할 수 있는 전이중 통신. 이러한 정보 통신 방법을 단방향은 라디오, 반이중은 무전기, 전이중은 스마트폰이라 생각하고 외우니 더욱 쉽
게 이해할 수 있었다. 또한, 신호를 전송할 때 직렬 또는 병렬 방식을 이용한다고 하는데, 요즘에는 병렬 방식보다 직렬을 선호한다고
한다. (->과연 왜 그럴까?)
병렬 통신 같은 경우, 여러 선을 통해 여러 비트 데이터들을 동시에 전송하는 방식이다. 컴퓨터의 성능이 떨어
지던 시대에선 병렬 방식을 채택했을지 몰라도. 지금처럼 성능이 뛰어난 컴퓨터 체계에서 (특별한 상황을 제외
하고) 직렬 방식을 채택해도 별다른 큰 문제가 없기 때문에 요즘에는 병렬 방식을 잘 사용하지 않는다고 한다. (또한, 병렬 통신 -> 선 여러개 -> (수많은 선을 포함)선 굵기가 얇아짐 -> 속도 또한 느려짐)
-> 솔직히 병렬 통신을 (아예 사용 안 하진 않으므로) 사용하는 예가 궁금해져서 찾아봤다. 대표적으로 데이터
버스, 데이터 전송 케이블(ex: HDMI)가 있다고 한다. 많은 데이터를 한 번에 처리하고 싶을 때, 동기식 통신을 사용한다. 하지만 계산 방식이 (비동기보다) 복잡하고 그만큼 비용이 많이 드는 통신이며 수ᆞ송신 사이의 타이밍 조절이
필요하다는 단점이 있다. > 만약 데이터를 수신하는 쪽이 송신 쪽보다 받을(감당할) 수 있는 데이터의 크기가 작다면 어떻게 될까?
동기식 통신을 방법으로 채택하기엔 수ᆞ송신 사이의 교류 도중 문제가 발생할 것이다. 이런 문제를 해결하기
위해서 수ᆞ송신 간의 합의를 이룰 수 있는 비동기식 통신이 생겼다. 동기식보다 속도가 느리다는 단점이 있지만, 회로 복잡도가 단순하고 start-stop 방식을 사용하여 데이터를 받
을 수 있다는 장점이 있다. 

정보를 통신하는 방법 2 >________________________________________________________________________
UART ᆞ I2C ᆞ SPI 통신 ᆞᆞᆞ
(사실 동기ᆞ비동기 통신 개념을 들었을 때부터 머릿속이 어질어질 해졌는데 이것들을 짬뽕한 통신들이 여러
차례 쉬질 않고 나와서 기절할 뻔했다. 그래도 선생님께서 지금은 정리가 잘 안 되더라도 다음에 다시 볼 땐 익
숙해질 것이라고 말씀해주신 덕에 그 당시에는 어려웠지만, 지금 이 글을 적고 있는 지금, 다시 아이컨텍을 하
다보니 조금씩 이해가 좀 되는 것 같다.)
UART 통신은 – 비동기-직렬 통신. (병렬 데이터를 직렬화하여 통신하는 개별 집적 회로)
I2C 통신 – 반이중-동기-직렬 통신. (직렬 데이터 전송을 위한 SDA, 클럭을 전달하는 SCL 포함. -> 두 개의
핀으로 반이중 통신 가능)
SPI – 전이중-동기 통신. (마스터와 슬레이브 사이의 1:1 통신 가능 -> 경우에 따라 1:n 통신도 가능.)
선생님께서 유아트 통신을 너무나 많이 강조하셔서 관심을 가지게 되었다. 비동기 통신답게 (64비트 운영체제

기준) 한 번에 1byte씩 데이터의 전송이 가능하다고 한다. 이런 유아트 통신은 병렬 회로를 통해 받은 데이터
(byte)를 외부에 전달하기 위해 단일 직렬 비트로 변환하는 과정을 맡는다고 한다.
(이런 통신 방법을 만든 사람도 대단하고 실행하는 바탕이 되어주는 시스템도 참 대단한 것 같다...)

개발 환경 구축>________________________________________________________________________________
기본적인 이론들을 마치고, 우리는 본격적으로 마이크로프로세서 개발환경을 구축하는 시간을 가지기로 하였다. 우리는 STM사에서 제공하는 STM32CubeIDE 개발환경을 개발할 때 사용할 예정인데, CubeIDE는 뛰어난 개발환경 못지 않음에도 불구하고 무려 무료라는 엄청난 장점이 있다.(이 점은 방학 때 미리
공부해봐서 알고 있었음.)
STM사에서 굳이 손해보는 장사를 할려고 무료로 푼 것이 아니라. 자신들의 제품들을 사도록 유도하려는 똑똑
한 방식을 채택하였다는 점에서 나는 그들의 시장 운영방식이 너무나 대단해 보였다. 마프 개발을 하면서 우리는 HAL이라는 함수를 자주 보게 될 것인데,
(요즘에는 하드웨어의 성능이 너무나 뛰어나, 기계에게 맞출 필요없이 -> 최적화 보다는 가독성을 더 높인다고
한다. -> 그것이 바로 HAL.)
그리고 HAL 라이브러리의 대표적인 30개의 HAL 라이브러리는 필수적으로 외워야 한다고 한다. (고난의 길 스
타트.) 이 외에도 미들웨어 및 ST-LINK와 같은 용어들을 앞으로도 많이 보게 될 예정이다. _____________________________________________________________________________________________ 

이번 시간은 통신 관련하여 새롭게 배운 용어들도 많았고 개발환경을 구축하는데에 많은노력을 들여야 함을 배
웠다. 유독 새로운 개념들이 많다 보니 내 생각을 적다기보다는 내용을 정리하는 데에 급급했다는 점이 아쉬웠
다. 계속 반복 복습을 하면서 이해를 높이고 싶다.