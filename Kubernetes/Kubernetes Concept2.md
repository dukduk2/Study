# Kubernetes Concept2

### 쿠버네티스란?
컨테이너화된 워크로드와 서비스를 관리하기 위한 이식성이 있고, 확장 가능한 오픈 소스 플랫폼.

선언적 구성과 자동화를 모두 용이하게 해준다.
크고, 빠르게 성장하는 생태계.
쿠버네티스 서비스, 기술 지원 및 도구는 어디서나 쉽게 이용 가능.

Google이 2014년 쿠버네티스 프로젝트를 오픈소스화.
Google의 15여년에 걸친 대규모 운영 워크로드 운영 경험을 기반으로 만들어졌다.

### 쿠버네티스의 뜻
쿠버네티스는 '키잡이'나 '파일럿'을 뜻하는 그리스어에서 유래했으며, 이는 governor(통치자)와 cybernetic(인공두뇌학)의 어원이다.
K8s는 'ubernete' 8rmfwkfmf '8'로 대체한 약어이다.

### 쿠버네티스의 필요성과 쓰임
다양한 기능 : 컨테이너 플랫폼, 마이크로서비스 플랫폼, 이식성 있는 클라우드 플랫폼 등.

쿠버네티스는 컨테이너 중심의 관리 환경을 제공.
이 환경은 사용자 워크로드를 위해 컴퓨팅, 네트워킹 및 스토리지 인프라스트럭쳐를 오케스트레이션한다.
이는 PaaS(Platform as a Service)의 단순명료함에 IaaS(Infrastructure as a Service)의 유연함을 더해주며, 인프라스트럭쳐 제공자 간 이식을 가능하게 해준다.

### 어떻게 쿠버네티스가 플랫폼이 될 수 있는가?
개발자의 생산성을 극대화할 수 있도록 애플리케이션에 특화된 워크플로우를 최적화할 수 있다.
초기에 수용 가능한 애드혹 오케스트레이션은 대규모의 견고한 자동화를 필요로 하곤 한다.
이것이 쿠버네티스가 애플리케이션을 더 쉽게 배포하고, 스케일링하며, 관리하는 컴포넌트와 툴의 생태계를 만드는 플랫폼의 기능을 하도록 설계된 이유이다.

Label은 사용자가 원하는 방식대로 자원을 정리할 수 있도록 해준다.

Annotation은 자원에 사용자 정의 정보를 추가해서 사용자의 워크플로우에 활용할 수 있도록 하고, 관리 툴이 상태를 쉽게 체크할 수 있는 방법을 제공해 준다.

Kubernetes Control Plane은 개발자와 사용자가 공통으로 사용할 수 있는 API를 기반으로 하고 있다.
사용자는 범용의 명령줄 도구를 대상으로 하는 자체 API를 가진 스케줄러와 같은 사용자만의 컨트롤러를 작성할 수 있다.

이 설계를 통해 쿠버네티스 위에 많은 다른 시스템을 올릴 수 있게 된다.

### 쿠버네티스가 아닌 것
쿠버네티스는 전통적인, 모든 것이 포함된 PaaS가 아니다.
쿠버네티스는 하드웨어 수준보다는 컨테이너 수준에서 운영되기 때문에, PaaS가 일반적으로 제공하는 배포, 스케일링, 로드 밸런싱, 로깅 및 모니터링과 같은 기능에서 공통점이 있기도 하다. 하지만, 쿠버네티스는 monolithic하지 않아서, 이런 기본 솔루션이 선택적이며 추가나 제거가 용이하다.
쿠버네티스는 개발자 플랫폼을 만드는 구성 요소를 제공하지만, 필요한 경우 사용자의 선택권과 유연성을 지켜준다.


#### 쿠버네티스는
 지원하는 애플리케이션의 유형을 제약하지 않는다. stateless워크로드, stateful워크로드, 데이터 처리를 위한 워크로드를 포함해서 극단적으로 다양한 워크로드를 지원하는 것을 목표로 한다. 애플리케이션이 컨테이너에서 구동될 수 있다면, 쿠버네티스에서 매우 잘 동작할 것이다.
 
 소스 코드를 배포하지 않으며 애플리케이션을 빌드하지 않는다. 지속적인 통합, 지속적인 배포(Delivery, Deployment)(CI/CD) 워크플로우는 기술적인 요구사항은 물론 조직 문화와 취향에 따라 결정된다.
 
 미들웨어(ex 메시지 버스), 데이터 처리 프레임워크(ex Spark), 데이터베이스(ex mysql), 캐시 또는 클러스터 스토리지 시스템(ex Ceph)와 같은 애플리케이션 레벨의 서비스를 제공하지 않는다. 이런 컴포넌트는 쿠버네티스 상에서 구동될 수 있고, 쿠버네티스 상에서 구동 중인 애플리케이션이 Open Service Broker와 같은 이식 가능한 메커니즘을 통해 접근할 수도 있다.
 
 로깅, 모니터링 또는 경보 솔루션을 포함하지 않는다. 개념 증명을 위한 일부 통합이나, 메트릭을 수집하고 노출하는 메커니즘을 제공한다.
 
 기본 설정 언어/시스템(ex jsonnet)을 제공하거나 요구하지 않는다. 선언적 명세의 임의적인 형식을 목적으로 하는 선언적 API를 제공한다.
 
 포괄적인 머신 설정, 유지보수, 관리, 자동 복구 시스템을 제공하거나 채택하지 않는다.
 
추가로, 쿠버네티스는 단순한 오케스트레이션 시스템이 아니다.
사실, 쿠버네티스는 오케스트레이션의 필요성을 없애준다.
오케스트레이션의 기술적인 정의는 A를 먼저 한 다음, B를 하고, C를 하는 것과 같이 정의된 워크플로우를 수행하는 것이다.
반면에, 쿠버네티스는 독립적이고 조합 가능한 제어 프로세스들로 구성되어 있다.
이 프로세스는 지속적으로 현재 상태를 입력받은 의도된 상태로 나아가도록 한다. A에서 C로 어떻게 갔는지는 상관이 없다.
중앙화된 제어도 필요치 않다.
이로써 시스템이 보다 더 사용하기 쉬워지고, 강력해지며, 견고하고, 회복력을 갖추게 되며, 확장 가능해진다.

### 왜 컨테이너인가?
애플리케이션을 배포하는 구식의 방법은 운영 체제의 패키지 관리자를 사용해서 애플리케이션을 호스트에 설치하는 것이었다.
이 방식은 애플리케이션의 실행 파일, 설정, 라이브러리 서로 간의 라이프사이클과 호스트 OS와 얽히게 된다는 단점이 있다.
예측 가능한 롤아웃과 롤백을 위해서 불변의 가상 머신 이미지를 만들 수도 있지만, VM은 너무 크고 이식이 불가능하다.

새로운 방법은 하드웨어 가상화가 아닌 운영 체제 수준의 가상화에 기반한 컨테이너를 배포하는 것이다.
이 컨테이너는 서로 격리되고 호스트와도 격리된다.
컨테이너는 컨테이너 자체의 파일시스템을 갖고, 다른 컨테이너의 프로세스를 알 수 없으며, 연산에 필요한 자원을 제한할 수 있다.
VM보다 빌드하기 쉬우며, 기반이 되는 인프라스트럭쳐와 호스트 파일시스템에서 디커플되었기(decoupled) 때문에 클라우드나 OS 배포판 간 이식성이 있다.

컨테이너는 작고 빠르기 때문에, 애플리케이션 각각을 컨테이너 이미지로 패키지할 수 있다.
이렇게 애플리케이션과 이미지를 일대일 관계를 갖도록 하면 컨테이너의 혜택을 만끽할 수 있게 된다.
불변의 컨테이너 이미지는 배포 시점이 아닌 빌드/릴리즈 시점에 만들어질 수 있다. 왜냐하면 각각의 애플리케이션은 애플리케이션 스택 외의 나머지 요소와 조합될 필요가 없기 때문이고, 운영 인프라스트럭처 환경에 밀접하게 결합시킬 필요도 없기 때문이다.
컨테이너 이미지를 빌드/릴리즈 시점에 생성하게 되면 개발 환경부터 운영 환경까지 일관된 환경을 가져갈 수 있게 된다.
마찬가지로, 컨테이너는 VM보다 훨씬 더 투명해서 모니터링과 관리가 용이하다.
컨테이너의 프로세스 라이프사이클이 수퍼바이저 프로세스에 의해 컨테이너 내에 감추어지지 않고, 인프라스트럭처에 의해 관리될 때 이는 더욱 용이해진다.
컨테이너마다 단일 애플리케이션을 담게 되면, 궁극적으로 컨테이너를 관리하는 것이 애플리케이션의 배포를 관리하는 것과 같아진다.

#### 컨테이너의 혜택 요약
기민한 애플리케이션 생성과 배포 : VM 이미지 사용 대비 컨테이너 이미지 생성이 보다 쉽고 효율적.

지속적인 개발, 통합 및 배포 : 안정적이고 주기적으로 컨테이너 이미지를 빌드해서 배포할 수 있고(이미지의 불변성 덕에) 빠르고 쉽게 롤백할 수 있다.

개발과 운영의 관심사 분리 : 배포 시점이 아닌 빌드/릴리즈 시점에 애플리케이션 컨테이너 이미지를 만들기 때문에, 애플리케이션이 인프라스트럭처에서 디커                          플된다.

가시성 : OS 수준의 정보와 메트릭에 머물지 않고, 애플리케이션의 헬스와 그 밖의 시그널을 볼 수 있다.

개발, 테스팅 및 운영 환경을 거친 일관성 : 랩탑에서도 클라우드에서와 동일하게 구동된다.

클라우드 및 OS 배포판 간 이식성 : Ubuntu, RHEL, CoreOS, on-prem, Google Kubernetes Engine 및 다른 어디에서든 구동된다.

애플리케이션 중심 관리 : 가상 하드웨어의 OS에서 애플리케이션을 구동하는 수준에서 OS의 논리적인 자원을 사용하여 애플리케이션을 구동하는 수준으로 추                        상화 수준이 높아진다.

느슨하게 커플되고, 분산되고, 유연하며, 자유로운 마이크로서비스 : 애플리케이션은 단일 목적의 머신에서 monolithic 스택으로 구동되지 않고, 보다 작고                                                            독립적인 단위로 쪼개져서 동적으로 배포되고 관리될 수 있다.

자원 격리 : 애플리케이션 성능을 예측할 수 있다.

자원 사용량 : 고효율 고집적