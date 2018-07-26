# 1. 안드로이드 아키텍쳐

안드로이드 애플리케이션 개발하기 위해서는 안드로이드의 전체적인 아키텍처를 알 필요가 있다고 생각한다.  
그래서 이 장에서는 안드로이드 아키텍쳐에 대해 알아볼 것이다.

## 1-1. 안드로이드 소프트웨어 스택

안드로이드 시스템은 소프트웨어 스택(Stack)의 형태로 구성된다.  
애플리케이션, 운영체제, 런타임 환경, 미들웨어, 각종 서비스와 라이브러리등이 겹겹이 모여 구성된 것이라고 생각할 수 있다.  
시각적으로 표현하면 아래 그림과 같다.  

![안드로이드 소프트웨어 스택](image/stack.png)

이제 스택의 각층에 대해 알아볼 것이다.

## 1-2. 리눅스 커널

소프트웨어 스택의 맨 밑에 위치한다. 리눅스 커널은 장치 하드웨어의 기반 운영체제 역할을 담당한다. 멑티태스킹을 지원하고 메모리 관리와 프로세스 실행 및 관리 등을 처리하는 핵심 시스템 서비스를 비롯해서 네트워크 인터페이스와 각종 하드우어 이터페이스를 위한 장치 드라이버를 제공한다. 

안드로이드는 리눅스의 커널만 사용한다. 원래 리눅스는 데스크톱이나 서버의 컴퓨터에서 사용하기 위해 개발되었다. 실제로 지금은 리눅스가 엔터프라이즈 서버 환경에서 널리 사용된다. 또 리눅스 커널의 효율성과 성능이 좋으므로 안드로이드 소프트웨어 스택의 핵심으로 모바일 장치에서도 사용된다.

## 1-3. 안드로이드 런타임 - ART

안드로이드 스튜디오에서 애플리케이션이 빌드될 때는 바이트 코드 형태(DEX, Dalvik Executable)로 컴파일된다.  
장치에 애플리케이션이 설치될 때 안드로이드 런타임(ART, Android RunTime)이 AOT(Ahead-Of-Time) 컴파일을 수행하여 바이트 코드를 장치의 프로세서(CPU)가 필요로 하는 네이티브 명령어(기계어)로 일괄 변환한다.  이렇게 변환된 형태를 ELF(Excutable and Linkable Format)라고 한다. 따라서 애플리케이션이 런칭될 때마다 ELF 버전으로 실행되므로 애플리케이션의 실행 속도가 더 빠르고 배터리 수명도 향상된다.

5.x(롤리팝) 버전에서는 애플리케이션이 런칭될 때마다 JIT(Just-in-Time) 컴파일 방법을 사용하여 달빅 가상머신(VM, Virtual Machine)에서 바이트 코드를 하나씩 기계어로 변환하면서 실행하였다.

## 1-4. 안드로이드 라이브러리

문자열 처리, 네트워킹, 파일 처리와 같은 일반적인 작업을 지원하기 위해 제공되는 표준 라이브러리에 추가하여 안드로이드 개발 환경에는 안드로이드 라이브러리도 포함된다. 이는 안드로이드 애플리케이션 개발에 특화된 다양한 자바 기반 라이브러리다. 이 부류의 라이브러리 예로는 애플리케이션 프레임워크 라이브러리를 포함하여 사용자 인터페이스 생성, 그래픽 드로잉, 데이터베이스 엑세스 등을 가능하게 해주는 라이브러리가 있다.

사용 가능한 핵심 안드로이드 라이브러리를 요약하면 다음과 같다.

- **android.app** - 애플리케이션 모델의 액세를 제공하며, 모든 안드로이드 애플리케이션의 초석이 되는 라이브러리다.

- **android.content** - 애플리케이션과 애프리케이션 컴포넌트 간의 콘텐트 액세스와 메시징을 가능하게 한다.

- **android.database** - 콘텐트 제공자가 게시한 데이터를 액세스하는 데 사용되고, SQLite 데이터베이스 관리 클래스를 포함한다.

- **android.graphics** - 생삭, 포인트, 필터 사각형, 캔버스를 포함하는 낮은 수준의 2D 그래픽 드로잉 API다.

- **android.hardware** - 가속도 센서와 광 센서 같은 하드웨어의 액세스를 제공하는 API를 나타낸다.

- **android.openhl** - OpenGL ES 3D 그래픽 렌더링 API의 자바 인터페이스다.

- **android.os** - 메세지, 시스템 서비스, 프로세스 간 통신을 포함하는 표준 운영체제 서비스의 액세를 애플리케이션에 제공한다.

- **android.media** - 오디오와 비디오의 재생을 할 수 있는 클래스 제공한다.