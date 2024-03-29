## Operating System QnA

### Q. 운영체제/목적
A. 컴퓨터 하드웨어 바로 위에 설치되어 사용자 및 다른 모든 소프트웨어와 하드웨어를 연결하는 소프트웨어 계층이다. 좁은 의미로는 커널 및 운영체제의 핵심 부분으로 메모리에 상주하는 부분이며 넓은 의미로는 커널과 각종 주변 시스템 유틸리티를 포함하는 개념이다. 운영체제의 목적은 컴퓨터 시스템 자원을 효율적으로 관리하는 것이 목적이다.

### Q. 운영체제 처리방식
A. Batch Processing은 작업 요청의 일정량을 모아서 한꺼번에 처리하며, 작업이 완전 종료될 때까지 기다려야 한다. Time Sharing은 여러 작업을 수행할 때 컴퓨터 처리 능력을 일정한 시간 단위로 분할하여 사용한다. Batch Processing에 비해 짧은 Response Time을 가지며, Iteractive 특징을 가지고 있다. Realtime OS는 정해진 시간 안에 어떠한 일이 반드시 종료됨이 보장(Deadline)되어야 하는 실시간 시스템을 위한 OS이다. 특수한 목적을 가지고 사용한다.

### Q. 운영체제 동시처리 용어
A. CPU는 1개당 1개의 작업을 처리하지만, 매우 빠른 시간안에 처리 되므로, 동시에 실행하는 것처럼 보이는 것은 Multitasking이다. 여러 프로그램이 메모리에 올라가 있는 것을 MultiProgramming이라 하며, CPU의 시간을 분할하여 나누어 쓴다는 의미는 Time Sharing이다. 마지막으로 하나의 컴퓨터에 CPU가 여러 개 붙어 있음을 의미하는 것은 MultiProcessor이다.

### Q. CLI/GUI
A. CLI는 Command-line Interface의 약자로, 명령어 인터페이스이다. 말 그대로, 명령어 기반의 운영체제이며 터미널을 통해 컴퓨터가 상호작용 하는 운영체제이다.

GUI는 Graphic-user Interface의 약자로, 그래픽 인터페이스다. 사용자가 편리하게 사용할 수 있도록 입출력 등의 기능을 알기 쉬운 아이콘 따위의 그래픽으로 나타낸 것이다.

### Q. Memory/CPU
A. 메모리는 CPU의 작업 공간이다. CPU는 평생 메모리에 접근하여 명령어를 실행하는 일만한다. 명령어 하나를 처리하면 Program Counter를 1 증가시켜 다음 명령어를 실행한다. CPU는 Device에 접근할 때 자신이 직접 접근하지 않고 Device Controller에게 요청한다.

### Q. Mode bit
A. 사용자 프로그램의 잘못된 수행으로 다른 프로그램 및 운영체제에 피해가 가지 않도록 하기 위한 보호장치가 필요했다. Mode bit을 통해 하드웨어적으로 두 가지 모드의 Operation을 지원한다.

Mode bit이 0일때는 CPU가 커널모드에서 수행중이므로, 모든 명령어를 수행할 수 있다. Mode bit이 1일때는 CPU가 사용자 프로그램을 수행중인 상태이며, Interrupt나 Exception 발생시 하드웨어가 Mode bit을 0으로 바꿔 운영체제에게 제어권을 넘긴다. 운영체제가 사용자 프로그램에게 제어권을 넘길 때는 넘기기 전에 Mode bit을 1로 세팅 후 넘긴다.

### Q. Timer
A. 특정 프로그램이 CPU를 독점하는 것을 보호한다. 타이머는 Time Sharing을 구현하기 위해 널리 이용되며, 현재 시간을 계산하기 위해서도 사용된다.

### Q. Device Controller
A. 해당 I/O 장치 유형을 관리하는 일종의 작은 CPU다. 데이터를 저장하는 Local Buffer와 제어 정보를 위한 Control Register를 갖는다. 화면에 출력할 데이터는 Local Buffer에 저장하고, 실제 화면에 출력하라는 명령은 Control Register에서 실행한다. I/O는 실제 Device와 Local Buffer 사이에서 일어나며 Device Controller는 I/O가 끝났을 경우 Interrupt를 발생시켜 CPU에게 그 사실을 알린다.

### Q. Direct Memory Access Controller
A. 원래는 CPU만 메모리에 접근할 수 있다. 하지만 그렇게 될시에 Interrupt의 발생빈도가 증가한다. 왜냐하면 I/O에서 뭔가 일이 끝날 때마다 Interrupt를 걸어주기 때문에, CPU가 아무리 빨라도 비효율적으로 일을 수행할 것이다. 그래서 Direct Memory Access Controller이 등장했고, I/O 작업을 메모리에 직접 접근하여 실행하고, CPU에게 Interrupt를 한 번만 걸어주어 발생 빈도를 줄인다.

### Q. 입출력 (I/O)
A. 모든 입출력 명령은 특권 명령이기 때문에 커널모드에서 수행을 해야한다. 하지만 사용자 프로그램이 수행될 때 입출력 요청이 필요하면, Interrupt를 발생시켜 CPU 제어권을 운영체제에게 넘긴다. 이 용어를 시스템콜이라고 한다. Trap을 사용하여 인터럽트 벡터의 특정 위치로 이동한 후, 제어권이 인터럽트 벡터가 가리키는 인터럽트 서비스 루틴으로 이동 후 올바른 입출력 요청인지 확인 후 수행하며 완료 시에는 제어권을 시스템콜 다음 명령으로 옮긴다.

### Q. Interrupt
A. 인터럽트는 두 가지로 나뉜다. 하드웨어 인터럽트는 하드웨어가 발생시킨 인터럽트이며, 주로 입출력에 대한 응답이다. 소프트웨어 인터럽트는 Trap이라 하며 사용자 프로그램이 발생시킨 인터럽트이다. 트랩은 또 두가지로 나뉘는데, 프로그램이 오류를 범한 경우에는 Exception, 프로그램이 커널 함수를 호출하는 경우는 System Call이라 한다.

### Q. 동기/비동기 입출력
A. 동기식 입출력은 I/O 요청 후 입출력 작업이 완료된 후에야 제어가 사용자 프로그램에 넘어간다. 비동기식 입출력은 입출력이 시작된 후 작업이 끝나기를 기다리지 않고 제어권이 사용자 프로그램에게 즉시 넘어간다. 두 경우 모두 입출력의 완료는 인터럽트로 알려준다.

### Q. 프로그램 실행
A. 프로그램이 실행되면 프로그램을 위한 주소가 0번부터 할당되고, 다른 프로그램이 실행되면 다른 프로그램을 위한 주소가 0번부터 할당된다. 즉, Virtual Memory가 형성되며 그 구조는 code, data, stack으로 이루어져있다. 당장 필요한 프로그램만 메모리에 올리고 나머지는 Disk에 내려둔다.

Code는 기계어이며, 자원 관리를 위한 코드, 시스템 콜, 인터럽트 처리 코드 등 편리한 서비스 제공을 위한 코드들이 있다. Data는 운영체제가 사용하는 여러 자료구조를 정의하거나, PCB 등이 있고, Stack은 각 프로세스의 커널 스택이다. 

사용자 프로그램에서 입출력 요청을 하면 커널모드로 들어간다. 응답이 오면 다시 사용자 모드로 돌아가고 다시 커널모드로 반복을 실행하고, 프로그램 종료시 끝난다.

### Q. 함수 메모리 영역
A. 사용자 정의함수, 라이브러리 함수는 자신이 실행시킨 프로세스의 Code 영역에 들어가며, 커널 함수는 커널의 Code 영역에 적재된다.

### Q. 프로세스
A. 프로세스는 실행중인 프로그램을 말한다. 프로세스의 문맥(Context)는 CPU 현재 상태를 나타내기 위해 필요한 모든 요소들이다.

### Q. 프로세스 상태
A. 프로세스가 생성중인 상태를 New라고 한다. 프로세스가 생성되어 CPU를 기다리는 상태는 Ready, CPU를 잡고 명령어를 수행중인 상태는 Running이라 한다. 수행이 끝난 상태를 Terminated 상태이며, CPU를 당장 주어도 명령어를 수행할 수 없는 상태, 즉 자신이 요청한 Event가 만족되지 않아 이를 기다리는 상태를 Blocked 상태라 한다. 마지막으로 외부적인 이유로 프로세스의 수행이 정지된 상태로, 중기스케줄러에 의해서 프로세스 통째로 디스크에 Swap out 된 상태이다.

### Q. 문맥교환 (Context Switch)
A. CPU는 굉장히 빠르다. 그래서 한 프로세스가 CPU를 독점하는 것이 아닌 짧은 시간 간격으로 교환이 일어난다. 프로세스가 CPU를 뺏기고, 다시 얻었을 때 처음부터 실행하는 것이 아닌, 뺏기던 시점의 문맥을 기억해뒀다가 그 시점부터 실행하는 메커니즘이다. 

### Q. 스케줄러
A. 스케줄러의 종류에는 세 가지가 있다. 어떤 프로세스를 메모리로 적재할 지 결정하는 장기 스케줄러가 있다. 즉, New 상태인 것을 Ready로 보내는 문제이다. 단기 스케줄러는 CPU를 주는 문제이다. Ready 상태에 있는 프로세스를 Running시킬지 결정하는 문제다. 마지막으로 중기 스케줄러는 메모리 여유 공간 마련을 위해 프로세스를 통째로 메모리에서 Swap out 시키는 것을 결정하는 스케줄러다.

### Q. 쓰레드
A. 프로세스 하나에 CPU 수행 단위만 여러 개를 두고 있는 것이다. 쓰레드는 Stack 부분을 제외한 나머지 부분을 공유한다. 쓰레드의 장점은 다중 쓰레드로 구성된 테스크 구조에서는 하나의 서버 쓰레드가 Blocked 상태인 동안에도 동일한 테스크 내의 다른 쓰레드가 실행되어 빠른 처리를 할 수 있다. 동일한 일을 수행하는 다중 쓰레드가 협력하여 높은 처리율과 성능 향상을 얻을 수 있다. 하지만 데이터를 공유한다는 점에서 동기화 문제를 해결해줘야 한다.

### Q. 프로세스 vs 쓰레드
A. 프로세스는 현재 메모리에 올라와서 실행중인 프로그램이고, 쓰레드는 프로세스의 실행 단위를 뜻한다. 각각의 프로세스는 독립적인 메모리를 갖고있는 반면 쓰레드는 스택 영역을 제외한 부분을 공유한다. 그래서 쓰레드 여러 개 생성해서 사용하는 멀티 쓰레드에서는 자원 생성과 관리의 중복을 최소화한다는 장점이 있지만 동기화 문제를 해결해줘야 한다.

### Q. CPU Scheduling
A. 여러 종류의 프로세스가 섞여 있기 때문에 스케줄링이 필요하다. CPU와 I/O 장치 등 시스템 자원을 골고루 효율적으로 사용해야 한다.

### Q. CPU Scheduler/Dispatcher
A. CPU Scheduler는 Ready 상태의 프로세스 중에서 이번에 CPU를 줄 프로세스를 고르는 것이며, Dispatcher는 제어권을 CPU Scheduler에 의해 선택된 프로세스에게 넘기는 과정을 말한다. 이 과정을 문맥교환이라고도 한다.

### Q. CPU 스케줄링이 필요한 경우
A. 실행중인 프로세스가 어떤 이벤트 발생으로 인해 Blocked 상태로 넘어갈 때, Timer Interrupt로 실행중인 프로세스가 CPU 할당시간이 만료 됐을 때, Blocked 상태에서 이벤트가 완료되어 Ready 상태일 때, 프로세스가 완전히 끝났을 때 스케줄링이 필요하다.

### Q. 스케줄링 성능 척도
A. 시스템 입장에선 CPU Utilization과 Throughput이 있다. 전자는 전체 시간 중 CPU가 놀지 않고 일한 시간의 비율, 즉 이용률을 말하며 후자는 주어진 시간동안 몇 개의 일을 처리했는가를 나타내는 처리량이다. 사용자 입장에서는 CPU를 쓰러와서 다쓰고 나갈 때까지의 시간인 Turnaround Time이 있고, CPU를 얻기까지 Ready Queue에서 대기한 시간인 Waiting Time, Ready Queue에 들어와서 처음 CPU를 얻기까지 걸린 시간인 Response Time이 있다.

### Q. FCFS
A. FCFS는 First-Come First-Serve의 약자로, 먼저 온 순서대로 처리하는 방식이다. 비선점형 방식이며 CPU를 오래 사용하는 프로세스가 먼저 와서 CPU를 할당 받으면 나머지 프로세스들은 전부 기다려야하기 때문에 비효율적이다.(Convoy Effect)

### Q. SJF/SRTF
A. SJF는 Shortest Job First의 약자로 각 프로세스의 CPU burst time을 가지고 스케줄링에 활용한다. CPU burst time이 가장 짧은 프로세스를 먼저 스케줄링하며, 가장 적은 대기 시간을 보장한다. 

Shortest Remaining Time First의 약자로, SJF와 비슷한데, 선점형이다. 현재 수행중인 프로세스의 남은 burst time보다 더 짧은 시간을 가지는 새로운 프로세스가 도착하면 CPU를 빼앗긴다. SJF와 SRTF의 문제점은 Starvation 문제가 발생한다. 짧은 프로세스들로 인해 긴 프로세스가 오랫동안 CPU를 잡지 못하는 현상이다.

### Q. Priority Scheduling
A. 우선순위가 가장 높은 프로세스에게 CPU를 할당하는 스케줄링이다. SJF는 일종의 Priority Scheduling이다. 문제점은 역시 Starvation이며 해결 방법은 Aging이다. Aging은 아무리 우선순위가 낮은 프로세스라 하더라도 시간이 오래 지나면 우선순위를 높여주는 것이다.

### Q. Round Robin
A. 각 프로세스는 동일한 크기의 Time Quantum을 가진다. 할당 시간이 지나면 프로세스는 선점 당하고 Ready Queue의 제일 뒤에 가서 다시 줄을 선다. Response Time이 빨라지며, Time Quantum이 큰 경우에는 FCFS와 유사하며, Time Quantum이 작은 경우에는 Context Switch 오버헤드가 커진다. 일반적으로 SJF보다 Turnaround Time이 길지만 Response Time은 더 짧다.

### Q. Multi-Level Queue
A. Ready Queue를 여러 개로 분할하는 방식이다. 큐에 대한 스케줄링이 필요하며, 각 큐에 CPU Time을 적절한 비율로 할당 해야한다.

### Q. Multi-Level Feedback Queue
A. MLQ와 비슷하지만, 프로세스가 다른 큐로 이동이 가능하다. MLFQ 방식으로 첫 Ready Queue는 Time Quantum을 짧게 하며, 가면 갈수록 길게하는 방식으로 Aging 구현이 가능하다. MLFQ를 정의하는 파라미터는 Queue의 수, 각 큐의 스케줄링 알고리즘, 프로세스를 상위 큐로 보내는 기준, 하위 큐로 보내는 기준, 프로세스가 CPU 서비스를 받으려할 때 들어갈 큐를 결정하는 기준이 필요하다.

### Q. MultiProcessor Scheduling
A. CPU가 여러 개인 경우에는 스케줄링이 더 복잡해진다. Homogeneous Processor인 경우에는 큐에 한줄로 세워서 각 프로세서가 알아서 꺼내가게 할 수 있다. 반드시 특정 프로세서에서 수행되어야 하는 프로세스가 있는 경우에는 복잡해진다. Load Sharing인 경우에는, 일부 프로세서에 Job이 몰리지 않도록 부하를 적절히 공유하는 메커니즘이 필요하다. 별개의 큐를 두는 방법과 공동 큐를 사용하는 방법이 있다. Symmetric MultiProcessing은 각 프로세서가 각자 알아서 스케줄링을 결정하며, Asymmetric MultiProcessing은 하나의 프로세서가 시스템 데이터의 접근과 공유를 책임지고 나머지 프로세서는 거기에 따르는 방식이다.

### Q. Real-Time Scheduling
A. Hard Real Time System은 정해진 시간 안에 반드시 끝내도록 스케줄링 하는 것이며, Soft Real Time Computing은 일반 프로세스에 비해 높은 우선순위를 갖도록 해야한다.

### Q. 데이터의 접근
A. 컴퓨터 시스템에서 데이터 연산은 저장 공간과 실행 공간이 따로 존재한다. 실제 저장 공간은 메모리나 해당 프로세스의 주소 공간, 디스크 등에 있고 실행 공간은 CPU나 프로세스, 컴퓨터 내부에 존재한다.

### Q. Race Condition
A. 저장 공간을 공유하고 실행 공간이 여러 개 있는 경우 Race Condition 가능성이 있다. 예를 들어 count를 1 증가하는 연산과 -1을 연산하는 공간이 있다고 가정하면, 여기서 증가시키는 연산을 수행하는 실행 공간에서 count를 가져와 증가시키고 감소하는 연산을 수행하는 실행 공간에서 count를 가져와 감소시키면 값은 그대로일 것이다. 하지만 증가시키는 연산을 수행하는 도중에 감소시키는 연산을 수행해서 증가시키는 연산이 먼저 끝나 count를 다시 돌려주고 감소시키는 연산의 결과를 다시 돌려주게 된다면 증가하는 연산과 관계없이 count는 감소한 값이 들어가있을 것이다. 이처럼 공유하는 하나의 주체에 여러 주체가 마치 경쟁하듯 접근하려 하는 것을 Race Condition이라 한다.

### Q. OS에서 Race Condition
A. Kernel 수행 중 인터럽트 발생 시 Race Condition이 발생할 가능성이 있다. Kernel에서 count++을 수행하던 도중(값을 저장하지 않은 상태), Interrupt가 발생하여 수행을 멈추고, 인터럽트로 넘어가게 된다. 인터럽트에서 count--를 수행하고 다시 커널로 돌아와 count++한 데이터를 저장하면 원래의 값이 나와야 하지만, 인터럽트에서 실행된 count--는 반영되지 않고, count++한 값만 저장이 된다. 이런 경우 인터럽트가 발생해도 커널에서 중요한 변수의 값을 작업하던 일이 저장이 될 때까지 수행될 수 있게끔 disable 해주어서 Race Condition을 막을 수 있다.

두 번째로 프로세스가 시스템콜을 호출하여 Kernel Mode로 수행 중인데 Context Switch가 일어난 경우이다. 커널 모드에서 count++ 연산 수행 도중에 Time Quantum이 끝나서 CPU 제어권이 넘어간다. CPU를 점유한 프로세스가 count++를 하고 다시 돌려주는데, 이때 최종 연산 결과는 count는 2가 증가되어야 하지만, 1만 증가하게 된다. CPU를 다시 할당받았을 때 그 시점의 Context를 가지고 값을 증가시켰기 때문이다. 이를 해결하기 위해서는 커널 모드에서 프로세스가 수행 중일때는 CPU 할당 시간이 끝나도 선점하지 않고 다시 사용자 모드로 돌아갔을 때 선점하다. (커널 - 비선점, 사용자 - 선점)

마지막으로 MultiProcessor에서 Shared Memory 내의 Kernel Data 사용이다. 이러한 경우 위의 두 방법으로 해결되지 않는다. CPU가 공유 데이터를 사용한다면 lock을 걸어 다른 CPU가 접근해도 접근할 수 없게 한다. 그리고 메모리에 저장할 때 unlock을 하여 다른 CPU가 접근하게 해줄 수 있다. 한 번에 하나의 CPU만 커널에 들어갈 수 있게 하는 방법은 비효율적이며, 커널 내부에 있는 각 공유 데이터에 접근할 때마다 그 데이터에 대한 lock/unlock 하는 것이 효율적이다.

### Q. The Critical-Section Problem
A. N개의 프로세스가 공유 데이터를 동시에 사용하기를 원하는 경우에 발생한다. 각 프로세스의 Code Segment에는 공유 데이터에 접근하는 코드인 Critical Section이 존재한다. 하나의 프로세스가 Critical Section에 있을 때 다른 모든 프로세스는 들어갈 수 없어야 한다.

### Q. Shared Memory Race Condition 해결법
A. 어떤 프로세스가 Critical Section 부분을 수행 중이면 다른 프로세스들은 들어갈 수 없게 해야한다.(Mutual Exclusion) 그리고 아무도 Critical Section에 있지 않은 상태에서 들어가고자 하는 프로세스가 있으면 들어가게 해주어야 한다.(Progress) 마지막으로 프로세스가 Critical Section에 들어가려고 요청한 후부터 해당 요청이 허용될 때까지 다른 프로세스들이 Critical Section에 들어가는 횟수는 한계가 있어야 한다.

### Q. Deadlock
A. 일련의 프로세스들이 서로가 가진 자원을 기다리며 Block된 상태를 의미한다. Deadlock을 발생하는 조건은 4개가 있다.

첫 번째로 매 순간 하나의 프로세스만이 자원을 사용할 수 있는 조건이다.(Mutual Exclusion) 두 번째로 프로세스는 자원을 스스로 내어놓을 뿐 강제로 뺏기지 않는 조건이다.(No Preemption) 세 번째로 자원을 가진 프로세스가 다른 자원을 기다릴 때 보유 자원을 놓지 않고 계속 가지고 있는 조건이다.(Hold and Wait) 마지막으로 자원을 기다리는 프로세스간에 사이클이 형성되어야 한다.(Circular Wait)

위의 4가지 조건 중 하나라도 만족하지 않으면 Deadlock이 발생하지 않는다.

### Q. Deadlock Prevention
A. Deadlock이 발생하는 네 가지 조건 중 하나를 원칙적으로 차단하여 발생을 미연에 방지하는 것이다.

Mutual Exclusion은 막을 수 있는 조건이 없다. Hold and wait는 프로세스가 자원을 요청할 때 다른 어떤 자원도 가지고 있지 않아야 한다. 즉, 자원이 필요한 경우 보유 자원을 모두 놓고 다시 요청한다. No Preemption은 선점형으로 바꾼다. Circular Wait는 모든 자원 유형에 할당 순서를 정하여 정해진 순서대로만 자원을 할당한다.

Deadlock을 막을수는 있지만 자원에 대한 Throughput은 떨어지고 Starvation 문제가 발생할 수 있다. 또한 제약조건이 많아져서 비효율적이다.

### Q. Deadlock Avoidance
A. 자원 요청에 대한 부가정보를 이용해서 자원 할당이 Deadlock으로부터 안전한지를 동적으로 조사해서 안전한 경우에만 할당한다. 가장 단순하고 일반적인 모델은 프로세스들이 필요로 하는 각 자원별 최대 사용량을 미리 선언하도록 하는 방법이 있다.(Banker’s Algorithm)

### Q. Deadlock Ignorance
A. 현재 대부분의 운영체제에서 채택한 방법으로 Deadlock이 발생하지 않는다 생각하고 아무런 조치도 취하지 않는 것이다. Deadlock은 매우 드물게 발생하기 때문에 조치를 취하는 것이 오히려 더 큰 오버헤드일 수 있기 때문이다. 만약 시스템에 Deadlock이 발생한 경우 시스템이 느려지거나 프로세스가 멈춘 것을 사용자가 느낄 수 있으므로 일부 프로세스를 직접 죽이는 등의 방법으로 대처한다.

### Q. Deadlock Detection and Recovery
A.  Deadlock 발생은 허용하되 그에 대한 Detection 루틴을 두어 Deadlock 발견시 Recover하는 방법이다. Recovery는 Deadlock에 연루된 프로세스들을 모두 죽이거나 연루된 프로세스들을 하나씩 죽이는 방법이 있다.

### Q. Memory Management
A. 메모리 관리는 운영체제가 하는 것이 아닌, 하드웨어적으로 해야 하는 역할들이다. CPU가 메모리에 접근할 때 CPU가 운영체제로 넘어가는 것이 아니기에 운영체제가 하는 역할은 아니다.

### Q. Virtual Address/Physical Address
A. Virtual Address는 프로세스마다 독립적으로 가지는 주소 공간이다. 각 프로세스마다 0번지부터 시작하며 CPU가 보는 주소다. Physical Address는 메모리에 실제 올라가는 위치다. 특정 프로그램이 물리적인 메모리에 어디에 올라갈 지 결정하는 것을 Address Binding이라 한다.

### Q. Address Binding
A. 프로그램이 물리적인 메모리에 어디에 올라갈 지 결정하는 것을 주소 바인딩이라 한다. 주소 바인딩에는 세 가지 방법이 있다.

Compile Time Binding은 물리적 메모리 주소가 컴파일 시 알려진다. 시작 위치 변경시 재 컴파일하며 절대 코드를 생성한다. 메모리를 재할당  할 때 다시 컴파일 해야하므로 비효율적이다.
Load Time Binding은 Loader 책임하에 물리적 메모리 주소를 부여한다. 컴파일러가 재배치 가능 코드를 생성한 경우에 가능하다.
Execution Time Binding(Run Time Binding)은 수행이 시작된 이후에도 프로세스의 메모리 상 위치를 옮길 수 있다. CPU가 주소를 참조할 때마다 Binding을 점검하며, 하드웨어적인 지원이 필요하다.

### Q. MMU
A. Memory Management Unit의 약자로, Virtual Address를 Physical Address로 매핑해주는 하드웨어 장치이다. MMU는 레지스터 두개를 통해서 주소를 변환한다. Base Register는 접근할 수 있는 물리적 메모리 주소의 값이며, Limit Registr는 Virtual Address의 범위이다. 매핑을 할때 Virtual Address 값을 Base Register 값을 더해 매핑한다.

CPU가 Virtual Address를 요청하면 Limit Register를 통해 프로그램보다 더 큰 주소를 요청한 것은 아닌지 확인한다. 만약 Limit Register에 있는 값을 벗어나는 요청이면 Trap이 걸린다.

### Q. Dynamic Loading
A. Loading은 프로세스를 메모리로 올리는 것이다. 프로세스 전체를 메모리에 미리 다 올리는 것이 아니라 해당 루틴이 불려질 대 메모리에 Load 하는 것을 Dynamic Loading이라 한다. Memory 이용률이 향상된다.

### Q. Overlays
A. 메모리에 프로세스의 부분 중 실제 필요한 정보만 메모리에 적재한다. 프로세스의 크기가 메모리보다 클 때 유용하다.

### Q. Swapping
A. 프로세스를 일시적으로 메모리에서 Backing Store로 쫓아내는 것이다. Backing Store(Swap Area)는 하드 디스크와 같이 충분히 빠르 큰 저장 공간이다.

### Q. Linking
A. Linking은 여러 군데에 존재하는 컴파일된 파일들을 묶어 하나의 실행 파일을 만드는 과정이다 Linking의 방법에는 두 가지가 있다.

Static Linking은 라이브러리가 프로그램의 실행 파일 코드에 포함되는 것이다. 실행 파일의 크기가 커지며 동일한 라이브러리를 각각의 프로세스가 메모리에 적재하므로 낭비가 된다.
Dynamic Linking은 라이브러리가 실행시 연결된다. 라이브러리 호출 부분에 라이브러리 루틴의 위치를 찾기 위한 stub이라는 작은 코드를 둔다. 라이브러리가 이미 메모리에 있으면 그 루틴의 주소로 가고 없으면 디스크에서 읽어온다. 운영체제의 도움이 필요하다.

예를 들어, 100명이 printf 함수를 호출했다고 가정하면 Static Linking을 사용하면 같은 기능을 하는 함수라도, 별도의 프로그램에 속한 것이기 때문에 100개 전부 메모리에 올라간다. 그에 반대로 Dynamic Linking은 누군가 printf를 호출해서 라이브러리를 메모리에 적재해놓은 경우 다른 사람들이 동일한 함수를 호출했을 때 공유해서 사용할 수 있다.

### Q. 메모리 할당
A. 메모리 할당은 고정 분할 방식과 가변 분할 방식이 있다. 고정 분할 방식은 프로그램이 들어갈 사용자 메모리 영역을 미리 나누어 놓는 것으로, External Fragmentation과 Internal Fragmentation이 발생한다. 가변 분할 방식은 프로그램이 실행될 때마다 차곡차곡 메모리 영역에 넣는 것이다. External Fragmentation 발생한다.

### Q. Paging
A. 프로그램을 구성하는 Virtual Memory를 동일한 Size의 Page 단위로 나누어 각 Page를 Physical Memory 빈 공간에 올리는것이다. 일부는 Backing Storage에 일부는 Physical Memory에 저장한다. Virtual Memory의 내용이 Page 단위로 불연속하게 저장된다.

### Q. Segmentation
A. 프로그램을 의미 단위인 여러 개의 Segment로 구성한다. 작게는 프로그램을 구성하는 함수 하나하나 크게는 프로그램 전체로 구성한다.

### Q. Demand Paging
A. 실제로 필요할 때 Page를 메모리에 적재하는 것이다. I/O 양 감소, 메모리 사용량 감소, 빠른 응답시간을 갖는다.

### Q. Page Fault
A. 사용중인 Page를 접근하면 MMU가 Trap을 발생시킨다. 커널 모드로 들어가서 Page Fault Handler가 Invoke된다. 만약 남는 Page가 없다면 뺏어온다.

### Q. Not Page Frame
A. 어떤 프레임을 빼앗아올지 결정해야 한다. 곧바로 사용되지 않을 페이지를 쫓아내는 것이 좋다. 동일한 페이지가 여러 번 메모리에서 쫓겨났다가 다시 들어올 수 있다. 그래서 Page Fault를 최소화 해야한다.

### Q. Offline Optimal Algorithm
A. Page Fault를 가장 적게 하는 알고리즘이다. 미래에 어떤 페이지가 참조될 지 아는 것은 불가능하다. 실제 시스템에서 사용될 수는 없고, 단지 미래에 참조되는 페이지를 전부 알고 있다고 가정한다. 아무리 좋은 알고리즘을 만들어도 이 알고리즘보다 좋을 수 없다.

### Q. FIFO
A. FIFO는 First-In First-Out의 약자로, 가장 먼저 들어온 것을 먼저 내쫓는다. 프레임 수를 늘렸음에도 불구하고 페이지 부재가 증가하는 현상이 발생한다.

### Q. LRU/LFU
A. LRU는 Least Recently Used의 약자로, 가장 오래 전에 참조된 페이지를 내쫓는다. LFU는 Least Frequently Used의 약자로, 참조 횟수가 가장 적은 페이지를 내쫓는다. 최저 참조 횟수인 페이지가 여럿이 있는 경우에는 임의로 선정한다. 성능 향상을 위해 가장 오래 전에 참조된 페이지를 지우게 구현할 수도 있다. LRU처럼 직전 참조 시점만 보는 것이 아니라 장기적인 시간 규모를 보기 때문에 페이지의 인기도를 좀 더 정확히 반영할 수 있다.

LRU 알고리즘은 연결리스트로 구현한다. 참조 시간 순서로 줄을 세워 아래로 갈수록 최근에 참조된 페이지라고 보면 된다. 새로운 페이지를 참조할 경우 맨 아래로 보내면 되고, 프레임이 꽉 차 페이지를 하나를 빼야 할 경우 맨 위 페이지를 제거하면 된다. 따라서 시간 복잡도는 O(1)이다.

LFU 알고리즘도 연결리스트로 구현할 수 있다. 하지만 참조 횟수 순서로 줄을 세울 경우 새로운 페이지를 참조했을 때 맨아래로 보내는 것이 아닌 다음 노드와의 횟수를 계속 비교해야 한다. 이와 같이 구현하면 O(N)의 시간 복잡도를 갖기 때문에 LFU 알고리즘은 힙으로 구현한다. 이로써 시간 복잡도를 O(logN)까지 줄일 수 있다.

### Q. 캐싱
A. Cache에 데이터를 저장해 두었다가 나중에 같은 데이터에 대한 요청이 왔을 때 느린 저장 장치까지 가지 않고 캐시로부터 바로 서비스 하는 방식이다. 시간 복잡도는 O(1)에서 O(logN)까지 허용한다.

운영체제는 Page Fault인 경우에만 관여한다. 즉 페이지가 이미 메모리에 존재하는 경우 페이지 참조 시각이나 페이지 참조 횟수 등의 정보를 운영체제가 알 수 없다. 따라서 LRU나 LFU와 같은 알고리즘을 페이징 시스템에서 사용할 수 없다.

### Q. Clock Algorithm
A. 페이징 시스템에서는 LRU나 LFU 알고리즘을 사용할 수 없고, 근사한 알고리즘인 Clock Algorithm을 사용한다. Linear한 Frame들을 Clock 처럼 Wrap Around 형태로 연결 시킨 후, 현재 가리키고 있는 임의의 페이지를 가리키는 Clock Hand로 페이지를 교체할 시점엔 어느 페이지를 선택할 지 결정해야 한다. (자세한 것은 블로그)

### Q. Thrashing
A. Page Fault Rate가 매우 높아져 CPU Utilization이 낮아지는 현상이다. 운영체제는 MPD를 높여야 한다고 판단하며 또 다른 프로세스가 시스템에 추가된다. 프로세스당 할당된 Frame 수가 더욱 감소하며 프로세스는 Page의 Swap In, Swap Out으로 매우 바쁘지만 CPU는 한가하다.

### Q. File/File System
A. 파일은 일반적으로 비휘발성의 보조기억장치에 저장한다. 운영체제는 다양한 저장장치 파일이라는 동일한 논리적 단위로 볼 수 있게 해준다. 메타데이터는 파일 자체의 내용이 아니라 파일을 관리하기 위한 각종 정보들이다. 파일 시스템은 운영체제에서 파일을 관리하는 부분이다. 파일 및 파일의 메타데이터, 디렉토리 정보등을 관리한다.

### Q. 버퍼캐시
A. 프로그램 A가 C라는 파일을 읽고 커널 메모리에 읽어와 복사한다. 프로그램 B가 다음으로 C라는 파일을 읽으려 할때 굳이 디스크까지 접근하지 않고 운영체제가 미리 읽어둔 내용을 전달하는 것이 버퍼캐시다.

### Q. Mounting
A. 서로 다른 파티션에 존재하는 파일 시스템을 접근 가능하게 해주는 것이다.

### Q. 연속할당
A. 파일을 할당할 때 Sector를 연속적으로 할당하는 방법이다. 한번의 Seek/Rotation으로 많은 바이트를 Transfer해서 빠른 I/O 시간을 갖는다. 하지만 External Fragmentation이 발생할 수 있고, File Grow가 어렵다.

### Q. Linked Allocation
A. 할당한 파일들의 Sector를 링크로 연결하는 것이다. External Fragmentation이 발생하지 않지만, 직접 접근이 어려우며, Seek시 많은 시간이 소요된다. 그리고 한 Sector이 고장나 Bad Sector가 되면 그 뒷 부분을 모두 잃는다.

### Q. Indexed Allocation
A. 인덱스 Sector를 하나 할당하고 해당 파일에 속하는 Sector들을 인덱스 Sector에 저장하는 방식이다. External Fragmentation이 발생하지 않고, 직접 접근이 가능하다. 하지만 파일이 굉장히 작은 경우에도 공간을 낭비한다. 굉장히 큰 파일의 경우에는 하나의 인덱스 블록으로 모두 표현이 불가능하다.

### Q. FAT File System
A. FAT은 Linked Allocation을 조금 변형한 것이다. Linked Allocation에서는 중간에 하나의 Sector가 Bad Sector가 되면 그 뒤에 있는 파일들을 읽지 못한다거나 포인터의 저장으로 공간 효율성이 낮아지는 단점이 있었다. 다음 블록의 위치 정보를 디렉토리 파일에 저장하지 않고 FAT에 저장해둠으로써 이러한 단점을 해결하고 직접 접근또한 가능하다.

### Q. Disk Structure
A. Logical Block은 디스크 외부에서 보는 디스크의 단위 정보 저장 공간들이다. Sector는 Logical Block이 물리적인 디스크에 매핑된 위치를 뜻한다.

### Q. Disk Access Time
A. Seek Time, 헤드를 해당 실린더로 움직이는데 걸리는 시간으로 가장 큰 시간 요소이다. Rotational Latency, 헤드가 원하는 섹터에 도달하기까지 걸리는 회전지연시간을 의미하며, Transfer Time, 실제 데이터의 전송 시간을 뜻한다. 따라서 Seek Time을 최소화 하는 것이 목표이다.

### Q. FCFS
A. First-Come First-Serve로 들어온 순서대로 처리한다. 비효율적이다.

### Q. SSTF
A. Shortest Seek Time First의 약자로, 현재 처리하고 있는 곳에서 가장 가까운 요청의 위치를 처리한다. Starvation 문제가 발생할 수 있다.

### Q. SCAN/C-SCAN
A. SCAN은 간단하면서 가장 쉽다. Disk Arm이 디스크의 한쪽 끝에서 다른쪽 끝으로 이동하며 가는 길목에 있는 모든 요청을 처리한다. 다른 한쪽 끝에 도달하면 역방향으로 이동하며 오는 길목에 있는 모든 요청을 처리하며 다시 반대쪽 끝으로 이동한다. 실린더 위치에 따라 대기 시간이 다르며, 가장자리에 있는 경우 대기 시간이 길다.

C-SCAN은 헤드가 한쪽 끝에서 다른쪽 끝으로 이동하며 가는 길목에 있는 모든 요청을 처리한다. 대신 다른쪽 끝에 도달했으면 요청을 처리하지 않고 곧바로 출발점으로 다시 이동한다. SCAN보다 균일한 대기 시간을 제공한다.

### Q. LOOK/C-LOOK
A. LOOK과 C-LOOK은 헤드가 진행중이거나 그 방향에 더 이상 기다리는 요청이 없으면 헤드의 이동 방향을 즉시 반대로 이동한다.

### Q. Disk Algorithm
A. SCAN, C-SCAN, LOOK, C-LOOK 등이 일반적으로 디스크 입출력이 많은 시스템에서 효율적이다. 디스크 스케줄링 알고리즘은 필요할 경우 다른 알고리즘으로 쉽게 교체할 수 있도록 OS와 별도의 모듈로 작성되는 것이 바람직하다.

### Q. RAID
A. Redundant Array of Independent Disks의 약자로, 여러 개의 디스크를 묶어서 사용하는 것이다. 여러 디스크에 block의 내용을 분산 저장하고, 병렬적으로 읽어와 디스크 처리 속도가 향상된다. 또한 동일 정보를 여러 디스크에 중복 저장하고, 하나의 디스크가 고장시 다른 디스크에서 읽어 올 수 있으며 단순한 중복 저장이 아니라 일부 디스크에 Parity를 저장하여 공간의 효율성을 높일 수 있어 신뢰성이 향상된다.




