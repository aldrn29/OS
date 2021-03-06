## 운영체제 시스템이란? 
컴퓨터 사용자와 컴퓨터 하드웨어 사이의 중개 역할을 하는 프로그램

#### 운영 체제 목표
- 사용자 프로그램을 실행하고 사용자 문제를 더 쉽게 해결한다.
- 컴퓨터 시스템을 사용하기 편리하게 만든다.
- 컴퓨터 하드웨어를 효율적으로 사용한다.

#### 컴퓨터 시스템의 요소
  1) 하드웨어: 기본 컴퓨터 자원을 제공한다.
  - Resource: 하나의 CPU 시간을 쪼개서 한 프로세스에게 할당하는 것 = time quantum
  - memory: 메인 메모리가 하나의 리소스라고 하기보다 쪼개서 하나의 프로세스가 차지하는 주소 공간을 말함
  - I/O devices
  2) OS: 다양한 유저를 위해 여러 가지 응용프로그램을 하드웨어 사이에 조절
  3) 응용 프로그램: 유저가 컴퓨터 문제를 해결하기 위한 시스템 리소스를 사용하고 정의
  4) 유저: 사람, 기계, 컴퓨터

#### Abstract(추상화)
- 추상화: 데이터와 상태까지 묶은 상태
- ((((하드웨어) OS) 응용프로그램) 유저): OS는 하드웨어 안의 여러 가지 자원들을 여러 유저가 동시 병렬로 사용할 수 있게 하고, 중간에서 조절/제어한다.

#### OS 정의
- 리소스 할당: 하드웨어 자원들을 관리하고, 응용 프로그램에 할당해준다.
- 프로그램을 조절: 유저 프로그램의 수행을 제어하고(유저가 프로그램을 돌리라는 부탁을 하면 OS가 종합하여 어떤 프로세스를 언제 돌릴지 순서를 정함), 한정된 I/O 디바이스를 동시에 요청하기 때문에 우선순위를 정하는 등 운영한다.
- 커널(OS의 핵심, 코어부분): 하나의 커널은 하나의 프로그램인데, 종료하지 않는 이상 항상 돌아간다. 커널 이외에 다른 것들은 다 어플리케이션 프로그램(or 시스템 프로그램)이라고 한다.

#### Mainframe 시스템(Cray 시스템)
- 유사한 작업들을 batching하여 setup 시간을 단축한다. (예: 수능답안지의 성적 처리)
- 자동으로 작업 순서 지정: 한 작업에서 다른 작업으로 제어 권한을 자동으로 이전한다. 최초의 초보적인 운영 체제이다.
- 프로세스 모니터링
  1) 처음에 프로세스가 돌아갈 때는 OS가 제어하다가,
  2) OS가 어플리케이션이 수행될 준비가 되면 제어를 job에게 던진다. (크롬 로딩 준비되면 크롬이 제어)
  3) 작업이 완료되면 모니터(OS)로 제어 돌아온다. (크롬이 종료되면 OS가 제어함)

#### Batch 시스템
- OS ---- 유저 프로그램
∙Multiprogrammed Batch 시스템
- 여러 개의 작업이 메인 메모리에 존재하고, CPU가 Multiplexed(시분할)하여 작업한다. 
  예) OS, 작업1, 작업2, 작업3, 작업4 (OS도 프로세스)

#### 다중 프로그램에 필요한 OS의 특징
- 시스템에 공급하는 입출력(I/O)
- 메모리 관리: 여러 개의 작업에 메모리를 할당한다.
- CPU 스케줄링: 여러 개의 준비가 되어있는 작업에서 시간을 선택, 할당해준다.
  예) 작업1 -> OS -> 작업2 -> OS...
- 나머지 하드웨어에서도 할당해준다. 

#### Time-Sharing 시스템, Interactive 컴퓨팅
- Interactive 컴퓨팅: 유저와 컴퓨터 사이의 대화하듯이 진행 
  예) 유저가 총을 쏘고 죽음, MS 워드 편집 등
- CPU가 많은 어플리케이션을 돌리는데, CPU는 이런 작업을 메인 메모리에 준비되어 있는 것들만 스케줄링 해준다.
- 메인메모리와 하드디스크 사이에 버스로 연결되어 있는데, 메인 메모리가 부족하면 쫒아(swapped out) 냈다가 여유가 생기면 다시 불러(swapped in)들인다.
- On-line 커뮤니케이션: 유저와 시스템 사이에서 인터렉션이 이루어지는 것이다. cmd창에서 대화식으로 이루어지는 것과 같이 명령이 끝나면 다음 명령을 기다린다.
- On-line 시스템: 유저가 주소공간(=프로세스 이미지)[데이터와 코드(Function)]에 접근할 수 있게 한다.

#### Desktop 시스템
- 사용자의 편의성, 응답성
- 개인 컴퓨터는 CPU의 활용도가 높지 않아도 된다.
- 여러 다른 타입의 운영체제를 사용할 수 있다. (윈도우, 맥OS, UNIX, Linux)

#### Parallel(병렬) 시스템
- CPU 이상의 기능을 갖춘 멀티프로세서 시스템
- Tightly coupled 시스템: 버스로 연결, 프로세서는 메모리와 Clock(동기화)를 공유하며, 일반적으로 공유 메모리를 통해 통신이 이루어진다.
- 병렬 시스템의 이점:
  1) 생산성 증가
  2) 경제적: I/O를 모두 공유함
  3) reliability 향상: 성능이 서서히 떨어짐, fail-soft 시스템 (하나가 고장이 나도 다른 것이 살아있기 때문에 비교적 대처를 잘함)
- 대칭형 멀티 프로세싱 (Symmetric multiprocessing: SMP)
  모든 CPU가 공통 OS를 사용하기 때문에 많은 프로세스가 성능의 저하 없이 돌린다. 
- 비대칭형 멀티 프로세싱 (Asymmetric multiprocessing)
  Mater CPU – Slave CPU 관계, 초대형 시스템에서 보통 쓰인다.

#### Distributed 시스템 (병렬시스템과 반대)
- Loosely coupled 시스템: 네트워크로 연결, 각 프로세서는 고유의 로컬 메모리를 가지고 있으며, 고속 버스나 전화선 같은 다야한 통신 라인을 통해 서로 통신한다.
- 분산 시스템의 이점:
  1) 리소스 공유
  2) Computation speed up – load 공유
  3) Reliability: 하나가 죽더라도 다른데서 실행하면 됨 (병렬시스템보다 더 좋음)
  4) 통신
- 네트워킹 인프라 필요
- LAN, WAN (Local/Wide area network)
- 클라이언트-서버, 피어-투-피어(예: 토렌트) 시스템

#### Clustered 시스템
- 스토리지를 공유하기 위해서 두 개 혹은 더 많은 시스템을 할당한다.
- high reliability
- 대칭형 clustering: 모든 n개의 host가 같은 일을 할 수 있을 때
- 비대칭형 clustering: 하나(Master)가 돌고, 나머지(Slave)는 대기를 하고 있을 때

#### Real-time 시스템
- 특정한 목적, 실험을 할 때 사용한다.
- Dead line, Fixed-time이 있어서 Dead line이 가까운 프로세스에게 더 많은 CPU를 할당해준다.
- Hard real-time: 빠르게 읽어와야 하기 때문에 모든 메모리가 메인메모리에 있거나 읽기 전용 메모리(ROM)에(RAM의 경우 읽어오는 게 느리기 때문) 있다. 동적으로 작업을 생성하지 않고 정해진 작업을 정의해놓고 진행한다.
- Soft real-time: 로봇 산업에서 제한적 효용성, 고급 운영체제 기능이 필요한 애플리케이션(멀티미디어, 가상 현실)에서 유용하다.

#### Handheld 시스템
- 메모리 한정, 프로세스 느림, 디스플레이 시스템이 작음
