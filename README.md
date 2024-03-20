# 이승환 202030122

## 2024-03-27
123123

## 2024-03-20
### 리엑트 개념  
- 복잡한 사이트를 **쉽고 빠르게 만들고 관리를** 위해 만들어진 것  
- 다른 표현으로 SPA를 쉽고 빠르게 만들 수 있도록 해주는 도구  

### 리엑트 장점  
* **빠른 업데이트와 렌더링 속도 (Virtual DOM 덕분에 가능)**   
    * DOM = XML, HTML 문서의 각 항목을 걔층으로 표현하여 생성, 변형, 삭제 할 수 있도록 돕는 인터페이스.
    * Virtual DOM = DOM이 속도가 느리기 때문에 고안된 방법
        * ***DOM은 동기식, Virtual DOM은 비동기식*** 

* **컴포넌트 기반 구조**  
    * 리엑트의 모든 페이지 = 컴포넌트
    * 하나의 컴포넌트는 여러개의 컴포넌트 조합으로 구성 가능
    * 리엑트로 개발 = 컴포넌트를 레고처럼 조합해서 웹사이트 개발

* **재사용성**
    * 반복적인 작업을 줄여줌 -> 생산성을 높여줌
    * 유지보수 용이
    * 재사용이 가능 하려면 해당 모듈의 의존성이 없어야 함

* **든든한 지원군**
    * 메타(***구 페이스북***)에서 오픈소스 프로젝트로 관리하고 있어 계속 발전 중

* **활발한 지식공유 & 커뮤니티**

* **모바일 앱 개발가능**
     리엑트 네이티브라는 모바일 환경 UI프레임워크를 사용하면 크로스 플랫폼 모바일 앱을 개발 할 수 있다.

### 리엑트의 단점
* **방대한 학습량**
    * 자바스크립트를 공부한 경우 빠르게 학습할 수 있다.

* **높은 상태 관리 복잡도**
    * state, component life cycle 등의 개념이 있지만 그리 어렵지 않다.

## 2024-03-13

a = ++b;  
=> b 값을 증가시킨 후에 대입

a = b++;  
=> b 값을 대입 한 후에 증가


// arrow  function expression을 사용  
const multiply = (a, b) =>{
    return a + b;
}
