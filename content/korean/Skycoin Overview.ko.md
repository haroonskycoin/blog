+++
title = "스카이코인 개요"
tags = [
    "Skycoin",
    "Statement",
]
bounty = 15
date = "2017-08-26"
aliases = [
	"/ko/overview/skycoin-overview/"
]
+++

<!-- MarkdownTOC autolink="true" bracket="round" depth="1" -->

- [스카이코인 소개](#skycoin-introduction)
- [비트코인과 현재 블록체인 프로토콜의 발전과 문제점](#innovations-and-flaws-with-bitcoin-and-the-current-blockchain-protocols)
- [비트코인에 의한 혁신](#innovations-produced-by-bitcoin)
- [비트코인의 주요 문제점](#major-flaws-of-bitcoin)
- [금융 원장을 위한 분산된 합의 시스템에 대한 바람직한 속성](#desirable-properties-for-systems-of-distributed-consensus-for-financial-ledgers)
- [스카이코인 보안 원칙](#skycoin-security-philosophy)
- [투명성과 보안 : Obelisk와 공개 브로드캐스트 채널](#transparency-and-security-obelisk-and-public-broadcast-channels)
- [Obelisk](#obelisk)
- [간단한 바이너리 합의 알고리즘 : 두 블록 사이에서 선택](#simple-binary-consensus-algorithm-choosing-between-two-blocks)
- [다중 동시 분기점 선택에 대한 합의](#consensus-on-multiple-concurrent-branch-choices)

<!-- /MarkdownTOC -->

# 스카이코인 소개

스카이코인은 공개 브로드캐스트 채널이라고 알려진 새로운 암호화
프리미티브를 도입한 기술을 기반으로 합니다.
이것은 또한 Obelisk라고 하는 새로운 합의 알고리즘 구현을 도입하여,
비트코인의 기반이 되는 작업 증명 및 마이닝 프로세스에서 발생하는
신뢰 문제를 완화시켜, 다음과 관련된 여러가지 보안문제를 해결합니다.
Obelisk는 단일 알고리즘이 아니며, 확실한 보안을 보장하기 위해 여러 기술이
사용되도록 구현되었습니다.

# 비트코인과 현재 블록체인 프로토콜의 발전과 문제점

비트코인에서는, 새로운 트랜젝션이 블록에 할당되어 블록 체인에 추가됩니다.
블록체인 네트워크의 모든 피어는 새 블록을 만들 수 있습니다.
따라서 각 블록에는 단일 부모 블록이 있지만
하나 이상의 유효한 하위 블록(자식)이 있습니다.
트리의 체인과 비트코인이 해결한 핵심 문제는 네트워크의
모든 노드가 합의 블럭체인인 체인 트리의 예상 체인 상에서 동의하는 것입니다.

비트코인은 고유한 블록체인을 결정하기 위해 작업증명(Proof-of-Work)라는 기술을 사용합니다.
유효한 블록에는 목표 값보다 낮은 해시 값이 필요합니다.
노드는 트랜잭션을 새 블록에 추가하고 블록에 대한
유효한 해시가 발견될 때까지 임의로 논스(nonces)를 시도합니다.

함수는 블록 트리에서 전체 체인 순서를 생성하는데 사용됩니다.
가장 난이도가 높고 해시 연산이 가장 많이 필요한 체인은
"가장 긴 체인"이며 합의 체인을 형성합니다.
"블록 깊이"와 "어려움"의 개념은 블록 트리의
모든 선형 체인에 대해 전체 순서를 만들고
가장 많은 자원을 소비하는 체인만이
합의 체인을 생성하도록 허용됩니다.

비트코인 노드는 서로 무작위로 연결되며 각 노드는
자신이 알고있는 가장 어려운 블록 체인을 다른 노드와 중계합니다.
한 노드가 다른 연결된 피어보다 체인을 생성하기가 더 어려울 경우
피어는 블록을 순차적으로 수신합니다.
피어는 기능을 평가하고 수신된 체인이 생산하기가 더 어려워서
수신된 체인에 대한 합의를 잠재적으로 전환할지
여부를 결정합니다.
다음에 그 피어는 새로운 체인을 동료에게 알립니다.
이러한 방식으로 합의가 네트워크 전체에 전파되고
모든 노드가 동일한 합의에 도달합니다.

비트코인은 노드에 ID가 있다고 가정하지 않으며
노드가 정직하다고 가정하지 않습니다.
노드는 다른 노드에 데이터를 전송할 수 있으며,
어려움은 자체 장점으로 독립적으로 검증될 수 있기 때문에
합의 결정에 영향을 미치지 않습니다.

# 비트코인으로 만들어진 혁신

### * 블록체인

모든 사람이 소유할 수 있는 단일 데이터 구조.

### * 거래를 위한 공용 원장

블록 체인에 금융 거래를 저장합니다.

### * PoW 및 난이도 재지정을 사용하여 일정한 블록 생산량 유지

### * 주소로 공개키 해시 사용

공개키는 사용될 때까지 공개되지 않습니다.

### * 화폐를 위한 "출력" 사용

분할 가능한 디지털 현금을 만들려고 시도하는 것을 무시합니다.:
25달러 출력에서 20 달러를 지불하려면 사람에게 20 달러를,
당신 자신에게 5달러를 되돌려 보내십시오.

### * PoW 난이도 함수 및 블록 깊이

블록 트리의 전체 순서를 정의하는 함수의 첫 번째 사용.
공개 원장은 전통적인 디지털 현금의 이중 지출 문제를 해결합니다.

# 비트코인의 주요 결함

이것은 새로운 암호화폐 방식을 개발할 때
반드시 해결해야 할 문제입니다.
비트코인은 미래 개발물들이 반드시 개선해야 할
기초적인 암호화폐로 간주되어야합니다.
스카이코인이 기반을 두고있는 기술은 전체 공유 시스템을
재설계함으로써 비트코인의 주요 결함을 해결합니다.

### * 비트코인의 합의 결정은 최종적이 아니며 되돌릴 수 있음

충분한 해싱파워를 임대 또는 구매할 수 있는
사람이나 조직은 거래를 되돌릴 수 있습니다.

### * 비트코인은 네트워크 합의를 달성하지만 개별 비트코인 노드는 패킷 통과 라우터를 제어하는 상대방에게 심각하게 취약함

라우터를 제어하는 상대방은 노드 관찰에 대한 절대적인 제어권을 가지며
노드의 합의 결정에 임의적으로 영향을 줄 수 있습니다.

### * 비트코인 거래는 공격에 심각하게 취약함

숙련된 공격자는 비트코인 거래소에서 51 %의 공격과
알트코인 매매를 통해 늦게 거래하는 사람을 파산시킬 수 있습니다.

### * 은행 및 도박 사이트가 51% 공격에 취약해졌음

### * 비트코인이 성장함에 따라, 비트코인에 대한 옵션 구매 및 네트워크에 대한 공격으로 수익이 발생함

미래에 비트코인에 대한 성공적인 공격은
옵션 거래로 수억 달러의 수익을 가져올 수 있습니다.

### * 강력한 자본 통제를 하는 국가들, 경쟁 기업들과 마찬가지로 비트코인 네트워크를 직접적으로 공격하여 금융 이익을 보호 할 수 있음

이러한 단체는 네트워크 공격 및 비트코인의 보안 비용을 쉽게 흡수할 수 있습니다.

### * "클라우드 해싱" 및 제3자 해시파워 대여 서비스가 점점 더 성공적으로 이루어지고 있음

많은 대형 풀에는 이제 다수의 공격에 대한
해시 파워를 임대할 수 있는 기능이 있습니다.

### * 해커들은 라우터와 네트워킹 장비에서 수많은 보안 취약점을 이용하여 은행과 거래소에서 코인을 훔칠 수 있음

공격자는 비트코인 노드에 연결된 피어를 제어하고
공격자가 제어하는 노드와의 연결을 보장할 수 있습니다.
예를 들어, 공격자는 은행 체인 한 쪽에 입금 트랜잭션을 생성하고,
은행에 출금 트랜잭션을 생성한 다음, 주 네트워크로 중계할 수 있습니다.

### * 비트코인은 낮은 비용으로 보안을 제공할 수 없음

비트코인 네트워크는 막대한 양의 전기를 사용하고 있습니다.
비트코인의 보안은 의도적으로 가능한 한
많은 전기를 낭비하는 것에 의존합니다.
보안은 대부분의 해시 비율을 달성하는데 드는
비용과 관련되므로 비트코인 네트워크를 실행하는 비용은
지속적으로 증가합니다.
잘 설계된 시스템에서는 $1의 보안 비용이
$1000의 비용을 능가합니다.
비트코인에서 이 비율은 $1는 $1입니다.
또한, 이것은 환경적으로 무책임합니다.

### * 비트코인은 근본적으로 보안을 손상시키지 않으면서 트랜잭션 시간을 줄일 수 없음

비트코인 트랜잭션은 블록에 포함되기까지
평균 10 분이 걸리고, 보안을 강화하려면
더 많은 시간이 필요합니다.

# 금융 원장을위한 분산된 합의 시스템에 대한 바람직한 속성

비트코인을 개선할 수 있는 기준은 다음과 같습니다.:

### * 이중 지출 없음

거래가 일단 실행되면 합의를 되돌릴 수 없어야 합니다.
합의는 가능한 한 되돌릴 수 없어야 합니다.

### * 효율성

완벽하게 안전한 원장을 운영하기위한
비용은 최대한 적어야 합니다.

### * 속도

시스템에서 트랜잭션을 몇 초 내에 확인할 수 있어야 합니다.

### * 투명성

이것은 악성 노드를 감사하고 식별하는 것을 간편하게 합니다.

### * 라우터 공격 보안

노드는 그들의 합의가 네트워크와 다른지에
대한 여부를 감지 할 수 있어야 합니다.

일부 보안 속성은 네트워크의 대다수 노드가 악성 및
담합인 경우에도 그대로 유지되어야합니다.

근본적인 수준에서, 비트코인 시스템과 관련된 많은
보안 문제는 작업 증명 및 채굴 프로세스의
고유한 약속 문제에서 비롯됩니다.
보안 문제는 실제-세계의 비잔틴 일반적인 문제를 나타냅니다.
해킹에 참여함으로써 참가자가 검증 프로그램을
조작할 수 있는 인센티브가 존재합니다.
공격자는 시스템 시간을 조작할 것이며,
라우터를 손상시키고, 해시 충돌을 사용하고,
수십만 개의 봇으로 네트워크를
넘치게 하고, 첨부된 서명을 날조합니다.

보안 시스템은 모든 알려진 공격으로부터 보호해야 할 뿐만 아니라
미래의 공격에 대응할 수 있을 정도로 견고해야 합니다.
첨부된 서명과 같은 비트코인의 일부 문제는 해결될 수 있습니다.
작업 증명 및 채굴자에 대한 의존도와 같은 다른 문제는 근본적이며, 완전히 새로운 프레임 워크를 정의하지 않고서는 해결할 수 없습니다.

# 스카이코인 보안 이론

보안은 위협에 대한 지속적인 식별 및 강화 프로세스입니다.
훌륭한 시스템은 "심층적인 방어"를 달성하고여러 중복 시스템을 가지며
모든 개별적인 척도에 대한 실패를 극복할 수 있습니다.
우수한 보안은 존재하는 위협과 단순한
성가신 위협 사이의 차별화를 필요로 합니다.

단일 시스템으로 모든 보안 위협을 제거하고
위에 나열된 모든 목표를 동시에 달성할 수는 없지만
스카이코인은 보안에 대한 모듈식 계층화된 접근법을 사용하고
특정 시스템을 사용하여 특정 보장을 실시하기 때문에
차세대 암호화폐로 대표됩니다.
스카이코인 보안은 비트코인이 직면한 실존적 위협을 해결하고
일상적인 위협으로부터 사용자를 보호하며
사용자, 이해 관계자 및 기관에서 가장 큰 손실을 낳을 수 있는
공격 클래스에 대해 최고 수준의 보호를 제공하는데 중점을 둡니다.
이를 위해서는 지갑 생성에서부터 합의를위한
블록 체인까지 비트코인을 완전히 재설계해야하며
근본적인 혁신이 필요합니다.

비트코인의 대부분의 손실은 소프트웨어 또는
수학의 근본적인 기술 공격보다는
디자인의 결함, 사용 편의성 부족 및 최종 사용자 실수로 인한 것입니다.
스카이코인은 비트코인에 존재하는 현실적인 수학적 위협과
비트코인의 불완전성과 일상적인 사용자를 위한 사용자 경험을
거의 고려치 않음에서 발생한 보안 문제를 모두 해결해야 합니다.
취약한 사용성과 디자인으로 인해 사용자는 일상적으로 안전하지
않은 웹 지갑의 보안에 수백만 달러가 달려있습니다.
일상적으로 언론에 의해 보고된 빈번한 절도에도 불구하고,
범죄자에 의해 훔쳐진 비트코인보다
더 많은 비트코인이 사용성 문제로 인해 없어졌습니다.

기존의 비트코인 중 절반 이상이 초기 주소에서 이동된 적이 없으며
복구할 수 없는 지갑 파일, 손실된 지갑 또는 실제로 지갑 파일에
백업된 내용에 대한 오류로 인해 손실될 수 있습니다.
Mt. Gox는 최근 그들이 알지 못하는 비트코인 지갑에서
200,000 비트코인을 "발견" 했다고 밝혔습니다.
그 지갑은 이전에 인식되지 않았으며,
실수로 쉽게 삭제될 수 있었습니다.
지갑은 자주 공백 오류를 일으키는데,
왜냐하면 지갑의 소프트웨어가 "너무 오래되어"
컴퓨터 소프트웨어가 그것을 로드 할 수 없기 때문입니다.
따라서 비트코인과 관련된 대부분의 보안 문제는 사용성,
최종 사용자 및 교환 보안 수준에서 발생합니다.

이 섹션의 나머지 부분에서는 네트워크 수준의 보안 문제를
해결하고 스카이코인 블록 체인을
이전 네트워크보다 더 안전하게 구현하기 위해 파트너와 협력하여
만든 몇 가지 새로운 기술에 대해 설명합니다.

우리는 시스템이 합의를 이루고,
우리가 원하는 보안 특성을 가지고 있으며,
정상적인 네트워크 조건에서 잘 작동한다는 것을
수학적으로 증명했습니다.
우리는 이전에 코인이나 소프트웨어에서 볼 수 없었던
흥미로운 새로운 데이터 구조를 가지고 있습니다.
현재 우리는 배포를 위해 시스템을
프로토 타입으로 만들고 있습니다.
스카이코인 개발 과정은 반복적입니다.
세부 사항을 작업하고, 알려진 결함을 해결하고,
시스템을 테스트하고 피드백을 얻으면서 변경, 개선될 것입니다.

# 투명성과 보안 : Obelisk 및 공개 방송 채널들

비트코인 시스템과 관련된 약속 문제를 해결하기 위해
스카이코인의 기술은 블록 채널을 공개 방송 채널 형태로
구현합니다. 모두가 체인을 읽을 수 있지만
소유자만이 블록을 작성할 수 있습니다.
개인 체인을 사용하려면 각 블록이
소유자 개인키로 서명되어야 합니다.
이 합의 알고리즘 시스템(Obelisk)의 각 노드는
개인 블록 체인을 가지고 있으며
Obelisk 시스템의 핵심 기본 요소입니다.

공개 방송 채널은 몇 가지 제약 조건을 부과합니다 :

### * 한 번 블록을 게시하면, 철회할 수 없음

블록은 모든 가입자에게 P2P(peer to peer)로 복제됩니다.
블록이 게시되면 모든 구독자에게 전파됩니다.
인터넷에서 지우려면 블록을 받은 모든 피어를 파괴해야 합니다.

### * 노드는 탐지되지 않고 이전 블록의 다른 버전을 게시 할 수 없음

노드가 동일한 시퀀스 번호를 가진 두 개의
다른 블록에 서명한 경우
블록에 번호가 매겨지고 탐지될 것입니다.

### * A 블록은 블록 발행을 지연시키지 않으면서 블록 수신 시 타임 스탬프를 되돌릴 수 없음

타임스탬프는 단지 올라갈 뿐이며,
타임 스탬프는 블록 시퀀스 카운트에 따라
단조롭게 증가합니다.

### * 체인의 중간에 있는 블록은 그 이후에 오는 모든 블록을 무효화하지 않고는 변경될 수 없음

해시 체인에서 각 블록 헤더는 이전 블록의 해시를 포함합니다.

# Obelisk


각 Obelisk 노드(스카이코인 합의 노드)는 공개키(식별자)와
개인 블록체인(공개 방송 채널)이 있습니다.
합의 결정 및 의사 소통은 각 Obelisk 노드의
개인 블록 체인 내에서 발생합니다.
이것은 노드가 하는 모든 것에 대한 공개 기록입니다.
이를 통해 커뮤니티는 속임수와 담합에
대한 노드를 감사할 수 있습니다.
커뮤니티는 네트워크에 대한 공격에 참여하는
노드를 식별할 수있는 방법을 제공하고
네트워크에서 의사 결정이 수행되는 방식과
의사 결정에 영향을 주는 노드를 공개합니다.

각 노드는 구독하는 다른 노드의 목록이 있습니다.
구독자가 많은 노드는 더 "신뢰를" 받으며
네트워크에 더 많은 영향을 줍니다.
커뮤니티가 네트워크를 대표하는 노드를 신뢰하지 않거나
네트워크 내의 권한이 너무 집중되어 있다고
(또는 충분히 집중되어 있지 않거나) 느끼면
커뮤니티는 네트워크의 신뢰 관계를 집합식으로
변경하여 네트워크의 권력 균형을
일괄적으로 조정할 수 있습니다.

노드 구독 관계는 무작위일 수도 있고/또는
신뢰 웹을 통해 형성될 수도 있습니다.
(당신이 신뢰할 수 있는 커뮤니티의 사람들과
당신이 알고 있는 사람들의 노드를 구독)

노드가 가입한 체인에서 새 블록을 받으면
게시하는 블록의 해시를 게시합니다.
이것은 블록 수신에 대한 대중의 승인입니다.
각 블록은 타임 스탬핑되고 다른 체인의 블록 참조를 참조합니다.
이것은 블록 인식의 밀집된 상호 링크 체인을 생성합니다.
이러한 연쇄는 인과 관계를 수립하고 다음 절에서 설명하는
분산 타임 스탬핑 시스템으로 작동할 수 있습니다.
이를 통해 네트워크에 데이터가 존재하지 않거나
네트워크에 게시되지 않았음을 증명하거나
특정 노드가 특정 시간 간격 동안 활성 또는 오프라인 상태임을
확인할 수 있습니다.

T현재의 Obelisk 합의 알고리즘은 Ben-Or의
무작위 합의 알고리즘을 기반으로합니다.

무작위 그래프(최악의 경우)에서의 Sybil 공격은 Sybil 노드가 합의를 제어할 수 있게 하지만
노드는 트랜잭션을 되돌릴 수 없기 때문에 네트워크를 공격하는 유일한 경제적 인센티브를 제거합니다.
실제 그래프에서 네트워크의 Sybil 저항은 실제로 매우 높고 노드를 실행하면
대역폭 측면에서 비용이 많이 들기 때문에 대형 봇넷이 금지됩니다.

신뢰 관계는 희소하며 철회될 수 있습니다.
공격의 경우 네트워크는 덜 신뢰할 수 있는 노드로의
연결을 끊고 신뢰할 수 있는 노드의 더 작은 코어로 계약함으로써
대응합니다. 각 노드의 개인 블록 체인에 의해 남겨진
공개 기록을 통해 공격에 참여하는 노드를 쉽게 식별할 수 있습니다.
공격하는 노드가 식별됨에 따라,
개인은 그 노드와의 관계를 끊어 그 영향을 줄입니다.
따라서 스카이코인 네트워크의 주요 이점은 다음과 같습니다.:

- 스카이코인 합의는 민주적이며 노드는 커뮤니티에 의해 운영됩니다.
- 스카이코인 노드 합의는 공개적입니다.
- 모든 노드는 커뮤니티 및 제 3자 감사에 대한 책임이 있습니다.
- 스카이코인 합의 시스템 내의 영향은 민주적이고 투명합니다.(그러나 동등하지 않음)

# 간단한 바이너리 합의 알고리즘 : 두 블록 사이에서 선택

각 투표 결정은 해시 쌍(A, B)입니다.
A는 블록의 부모 해시이고 B는 블록의 해시입니다.
각 노드는 합의 블록이어야 한다고 믿는 다음 블록에 투표합니다.
그것이 가입된 노드의 40 %가 합의를 위한 동일한 후보자를 갖는다면,
노드는 그 합의에 대한 동의를 그 블록으로 변경합니다.
노드는 합의에 도달 할 때까지 후보자 사이에서 무작위로 변경합니다.

# 다중 동시 분기 선택에 관한 합의

보다 진보된 시스템은 (A, B, P)를 게시하며,
여기서 P는 0에서 1까지의 값입니다.
모든 후속 작업의 P 값의 합은 1 입니다.
이렇게 하면 다중 체인 분기에 대한 동시 합의 결정이 가능합니다.

네트워크의 대다수 노드가 정직하다면,
그들은 또한 같은 합의에 수렴할 것입니다.

스카이 코인은 제한된 형태의 스테이크 증명을 가지고 있습니다.
우리는 거래 수수료가 더 많은 블록을 선호하여 투표를 지향합니다.

주어진 부모에 대해 두 가지 가능한 합의
선택이 있고 두 블록 모두 트랜잭션을 실행하면
두 블록 중 어느 블록이 네트워크에 의해 선택되었는지에
관계없이 트랜잭션이 효과적으로 실행됩니다.
초기 합의 결정의 회귀 확률은 블록 깊이에
따라 기하 급수적으로 감소합니다.