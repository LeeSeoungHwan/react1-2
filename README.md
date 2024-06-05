# 이승환 202030122

## 2024-06-05
* **Shared State**
    * Share state는 state의 공유를 의미한다
    * 같은 부모 컴포넌트의 state를 자식 컴포넌트가 공유해서 사용하는 것

* **Shared State 적용하기**
    * 하위 컴포넌트의 state를 부모 컴포넌트로 올려서 shared state를 적용한다
    * 이것을 Lifting State Up 이라고 한다
    * 이를 위해 먼저 Temperatureinput 컴포넌트에서 온도 값을 가져오는 부분을 다음과 같이 수정한다
    * 이렇게 수정하면 온도를 state에서 가져오지 않고 props를 통해 가져오게 된다
    * 또 한가지 컴포넌트의 state를 사용하지 않기 때문에 입력 값이 변경되었을 때 상위 컴포넌트로 변경된 값을 전달해 줘야 한다.

* **정리**
    * 상위 컴포넌트인 Calculator에서 온도와 단위를 state로 갖고,
    * 두개의 하위 컴포넌트는 각각 섭씨와 화씨로 변환된 온도와 단위, 그리고 온도를 업데이트하기 위한 함수를 props로 갖고 있다.
    * 이렇게 모든 컴포넌트가 state를 갖지 않고, 상위 컴포넌트로 올려서 공유하면 리액트를 더욱 간결하고 효율적으로 개발할 수 있습니다.
 
 * **합성**
    * 합성은 여러개의 컴포넌트를 합쳐서 새로운 컴포넌트를  만드는 것이다
    * 조합 방법에 따라 합성의 사용 기법은 다음과 같이 나눌 수 있다

* **Containment**
    * 특정 컴포넌트가 하위 컴포넌트를 포함하는 형태의 합성 방법이다
    * 컴포넌트에 따라서는 어떤 자식 엘리먼트가 들어올 지 미리 예상할 수 없는 경우도 있따
    * 범용적은 박스 역할을 하는 Sidebar 혹은 Dialog와 같은 컴포넌트에서 특히 자주 볼 수 있다.
    * 이런 컴포넌트에서는 children prop을 사용하여 자식 엘리먼ㅌ를 출력에 그대로 전달하는 것이 좋다
    * 이때 children prop은 컴포넌트의 props에 기본적으로 들어있는 shildren 속성을 사용한다
    * 다음과 같이 props.children을 사용하면 해당 컴포넌트의 하위 컴포넌트가 모두 children으로 들어오게 된다.

    ```
    function FancyBorder(props){
        return (
            <div className={'FancyBorder' + props.color}>
                {props.children}
            </div>
        )
    }
    ```
    * 리액트에서는 props.children을 통해 하위 컴포넌트를 하나로 모아서 제공해준다
    * 만일 여러개의 children 집합이 필요할 경우는 별도로 props를 정의해서 각각 원하는 컴포넌트를 넣어준다
    * 예와 같이 SplitPane은 화면을 왼쪽과 오른쪽으로 분할해 주고, App에서는 SplitPane을 사용해서 left, right 두 개의 props를 정의하고 있다
    * 즉 App에서 left, right를 props를 받아서 화면을 분할하게 된다, 이처럼 여러개의 children집합이 필요한 경우 별도의 props를 정의해서 사용한다.

* **Specialization**
    * 웰컴다이얼로그는 다이어로그의 특별한 케이스이다
    * 범용적인 개념을 구별이 되게 구체화 하는 것을 특수화라고 한다
    * 객체지향 언어에서는 상속을 사용하여 특수화를 구현한다
    * 리액트에서는 합성을 사용하여 특수화는 구현한다
    * 특수화는 범용적으로 쓸 수 있는 컴포넌트를 만들어 놓고 이를 특수한 목적으로 사용하는 방식이다


## 2024-05-22
* **리스트와 키**
    * 리스트는 자바스크립트의 변수나 객체를 하나의 변수로 묶어 놓은 배열과 같은 것
    * 키는 각 객체나 아이템을 구분할 수 있는 고유한 값
    * 리액트에서는 배열과 키를 사용하는 반복되는 다수의 엘리먼트를 쉽게 렌더링 할 수 있다

* **리스트의 키**
    * 리스트에서의 키는 리스트에서 아이템을 구별하기 위한 문자열 이다
    * 이 키는 리스트에서 어떤 아이템이 변경, 추가 또는 제거되었는지 구분하기 위해 사용한다
    * 키는 같은 리스트에 있는 엘리먼트 사이에서만 고유한 값이면된다

* **폼**
    * 폼은 일반적으로 사용자로부터 입력을 받기위한 양식에서 많이 사용된다

* **제어 컴포넌트**
    * 제어 컴포넌트는 사용자가 입력한 값에 접근하고 제어할 수 있도록 해주는 컴포넌트이다

    
## 2024-05-08
* **Arguemns 전달하기**
    * 함수를 정의할 때는 파라미터 혹은 매개변수, 함수를 사용할 때는
    아귀먼트 혹은 인수하고 부른다
    * ㅣ벤트 핸들러에 매개변수를 전달해야 하는 경우도 많다
    ```
    <button onClick={(event)=> this.deleteItem(id, event)}>삭제하기</button>
    <button onClick={this.deleteItem(this, id)}>삭제하기</button>
    ```
    * 위의 코드는 모두 동일한 역할을 하지만 하나는 화살표 함수를, 다른 하나는 bind를 사용한다
    * event라는 매개변수는 리액트의 이벤트 객체를 의미 한다
    * 두 방법 모두 첫 번째 매개변수는 id고 두 번째 매개변수로 event가 전달된다
    * 첫 번째 코드는 명시적으로 event를 매개변수로 넣어 주었고, 두 번째 코드는 id 이후 두 번째 매개 변수로 event가 자동 전달 된다
    
* **조건부 렌더링**
    ```
    function Greeting(props){
        const isLoggedIn = props.isLoggedIn;
        if(isLoggedIn){
            return <UserGreeting />;
        }
        return <GuestGreeting />;
    }
    ```
    * 이와 같은 렌더링을 조건부 렌더링이라 한다

* **엘리먼트 변수**
    * 렌더링해야 될 컴포넌트를 변수처럼 사용하는 방법이 엘리먼트 변수 이다.

* **인라인 조건**
    * 필요한 곳에 조건문을 직접 넣어 사용하는 방법
    1. 인라인 if
        * if문을 직접 사용하지 않고 동일한 효과를 내기 위해 && 논리 연산자를 사용한다
        * &&는 and연산자로 모든 조건이 참일때만 참이 됩니다
        * 첫 번째 조건이 거짓이면 두 번째 조건은 판단할 필요가 없다.

    2. 인라인 if-else
        * 삼항 연산자를 사용한다
        * 문자열이나 엘리먼트를 넣어서 사용할 수도 있다

* **컴포넌트 렌더링 막기**
    * 컴포넌트를 렌더링하고 싶지 않을 때에는 null을 리턴한다
    ```
    function WarningBanner(props){
        if(!porps.warning){
            return null;
        }
        return(
            <div>경고!</div>
        )
    }
    ```

## 2024-05-01
* **훅의 규칙**
    * 첫 번째 규칙은 무조건 최상위 레벨에서만 호출해야 한다.
    * 따라서 반복문이나 조건문 또는 중첩된 함수들 안에서 훅을 호출하면 안된다
    * 이 규칙에 따라서 혹은 컴포넌트가 렌더링 될 때마다 같은 순서로 호출이 되어야 한다
    * 두 번째 규칙은 함수형 컴포넌트에서만 훅을 호출해야 한다
    * 따라서 일반 자바스크립트 함수에서 훅을 호풀하면 안된다
    * 훅은 함수형 컴포넌트 혹은 직접 만든 커스텀 훅에서만 호출할 수 있다

* **나만의 훅 만들기**
    * 커스텀 훅을 만들어야 하는 상황
    * 한가지 주의할 점은 일반 컴포넌트와 마찬가지로 다른 훅을 호출하는 것은 무조건 커스텀 훅의
    최상위 레벨에서만 해야 한다.
    
* **DOM과 react에서의 이벤트 처리하는 차이**
    * 이벤트 이름이 onclick에서 onClick으로 변경
    * 전달하려는 함수는 문자여에서 함수 그대로 전달
    * 이벤트가 발생했을 때 해당 이벤트를 처리하는 함수를 이벤트 핸들러 라고 한다. 또는 이벤트가 발생하는 것을 계속 듣고 있다는 의미로 이벤트 리스너 라고 부르기도 한다.

* **이벤트 핸들러 추가 방법**
    * 버튼을 클릭하면 이벤트 헨들러 함수임 handleClick()함수를 호출하도록 되어 있음
    * bind를 사용하지 않으면 this.handClick은 글로벌 스코프에서 호출되어, undefined으로 사용할 수 없기 때문
    * bind를 사용하지 않으려면 화살표 함수를 사용하는 방법도 있다(
    ```
    class Toggle extends React.Component{
        constructor(props){
            super(props);
            this.state={isToggle: true};
            this.handClick = this.handClick.bind(this);
        }

        handleClick(){
            this.setState(prevState =>({
                isToggleOn: !prevState.isToggleOn
            }));
        }

        render(){
            return(
                <button onClick={this.handleClick}>
                    {this.state.isToggle ? '켜짐' : '꺼짐'}
                </button>
            )
        }
    }
    ```


## 2024-04-17
* **훅이란**
    * 클래스형 컴포넌트에서는 생성자에서 state를 정의하고, setSatate()함수를 통해 state를 업데이트함
    * 예전에 사용하던 함수형 컴포넌트는 별도로 state를 정의하거나, 생명주기에 맞춰서 코드가 실행되도록 할 수 없었다
    * 함수형 컴포넌트에서도 state나 생명주기 함수의 기능을 사용하게 해주기 위해 추가된 시능이 훅이다
    * 함수형 컴포넌트도 훅을 사용하여 클래스형 컴포넌트의 기능을 모두 동일하게 구현할 수 있게 됨
    * 훅이란 state와 생명주기 기능에 갈고리를 걸어 원하는 시점에 정해진 함수를 실행되도록 만든 함수
    * 훅의 이름은 모두 use로 시작한다
    * 사용자 정의 훅을 만들 수 있으며, 이 경우에 이름은 자유롭게 할 수 있으나 use로 시작할 것을 권장함

* **useState**
    * useState는 함수형 컴포넌트에서 state를 사용하기 위한 훅이다
    
* **useEffect**
    * useState와 함께 가장 많이 사용하는 훅이다
    * 이 함수는 사이드 이펙트를 수행하기 위한 것이다
    * 영어로 side effect는 부작용을 의미한다. 일반적으로 프로그래밍에서 사이트 이펙트는 개발자가 의도하지 않은 코드가 실행되면서 버그가 발생하는 것을 의미한다
    * 리엑트에서는 효과 또는 영향을 뜯하는 effect의 의미에 가깝다
    * 예를 들면 서버에서 데이터를 받아오거나 수동으로 Dom을 변경하는 등의 작업을 의미한다
    * 이 작업을 이펙트라고 부르는 이유는 이 작업들이 다른 컴포넌트에 영향을 미칠 수 있으며 렌더링 중에는 작업이 완료될 수 없기 때문이다. 렌더링이 끝난 이후에 실행되어야 하는 작업들이다
    * 클래스 컴포넌트의 생명주기 함수와 같은 기능을 하나로 통합한 기능을 제공
    * 결국 sideEffect는 렌더링 외에 실행해야 하는 부수적인 코드를 말한다
    * 예를 들면 네트워크 리퀘스트, Dom수동 조작, 로깅 등은 정리가 필요없는 경우 들이다

* **useEffect 사용법**
    * 첫 번째 파라미터는 이펙트 함수가 들어가고, 두 번째 파라미터로는 의존성 배열이 들어간다
    * 의존성 배열은 이펙트가 의존하고 있는 배열로, 배열 안에 있는 변수 중에 하나라도 값이 변경되었을 때 이펙트 함수가 실행됨
    * 이펙트 함수는 처음 컴포넌트가 렌더링 된 이후, 그리고 재 렌더링 이후에 실행된다.
    * 만약 이펙트 함수가 마운트와 언마운트 될 때만 한 번씩 실행되게 하고 싶으면 빈 배열을 넣으면 된다. 이경우 props나 state에 있는 어떤 값에도 의존하지 않기 때문에 여러 번 실행되지 않는다.

* **useMemo**
    * useMemo() 혹은 Memoized value를 리턴하는 훅이다
    * 이전 계산값을 갖고 있기 때문에 연산량이 많은 작업의 반복을 피할 수 있다
    * 이 훅은 렌더링이 일어나는 동안 실행된다
    * 따라서 렌더링이 일어나는 동안 실행되서는 안될 작업을 넣으면 안된다
    * ex) useEffect에서 실행되어야 할 사이드 이펙트 같은 것

* **useRef**
    * useRef()훅은 레퍼런스를 사용하기 위한 훅이다
    * 레퍼런스란 특저 컴포넌트에 접근할 수 있는 객체를 의미한다
    * useRef() 훅은 바로 이 레퍼런스 객체를 반환한다
    * 레퍼런스 객체에는 current라는 속성이 있는데, 이것은 현재 참조하고 있는 엘리먼트를 의미한다
    ```
    const reFContainer = useRef(초깃값);
    ```
    * 이렇게 반환된 레퍼런스 객체는 컴포넌트의 라이프타임 전체에 걸쳐서 유지된다.
    * 즉, 컴포넌트가 마운트 해제 전까지는 계속 유지된다는 의미
    
## 2024-04-03
* **Props 사용법**
    * JSX에서는 key-value 쌍으로 props를 구성한다.
    ```
    function App(props){
        return{
            <profile
                name = "소풀"
                introduction="안녕하세요, 소풀입니다."
                viewCount = (1500)
            />
        };
    }
    ```
    * profile 컴포넌트로 전달해서 name, inroduction, viewCount Props를 전달한다.
    * 이때 전달되는 props는 자바스크립트이다.

    * JSX에서는 중괄호를 사용하면 JS 코드를 넣을 수 있다.
    * 다음 코드처럼 props를 통해서 value를 할당 할 수 있고, 직접 중괄호를 사용하여 할당할 수도 있다.
    ```
    function App(props){
        return{
            <Layout
                width = (2500)
                height = (1400)
                header = {
                    <header title="소풀의 블로그입니다."/>
                }
                footer={
                    <Footer/>
                }
            />
        };
    }
    ```

* **컴포넌트의 종류**
    * 리액트 초기버전을 사용할 때는 클래스형 컴포넌트를 주로 사용했다.
    * 이후 K=Hook이라는 개념이 나오면서 최근에는 함수형 컴포넌트를 주로 사용한다.
    * 예저네 작성된 코드나 문서들이 클래스형 컴포넌트를 사용하고 있기 때문에,  
        클래스형 컴포넌트와 컴포넌트의 생명주기에 관해서도 공부해 두어야 한다.
    
* **컴포넌트 이름짓지**
    * 이름은 항상 대문자로 시작
    * 리애트는 소문자로 시작하는 컴포넌트를 DOM 태그로 인식하기 때문이다
    * ***컴포넌트 파일 이름과 컴포넌트 이름은 같게 한다***

* **컴포넌트의 렌더링**
    * 코드는 다음과 같다
    ```
    function Welcome(props){
        return <h1>안녕, {props.name}</h1>
    }

    const element = <Welcome name="인재" />;
    ReactDOM.render(
        element,
        document.getElementById('root')
    );
    ```

* **컴포넌트 합성**
    * 컴포넌트 합성은 여러개의 컴포넌트를 합쳐서 하나의 컴포넌트를 만드는 것
    * 리액트에서는 컴포넌트 안에 또 다른 컴포넌트를 사욜할 수 있기 때문에, 복잡한 화면을 여러개의 컴포넌트로 나누어 구현할 수 있다.

* **컴포넌트 추출**
    * 복잡한 컴포넌트를 쪼개서 여러 개의 컴포넌트로 나눌 수도 있다
    * 큰 컴포넌트에서 일부를 추출해서 새로운 컴포넌트를 만든다
    ***실무에서는 처음부터 1개의 컴포넌트에 하나의 기능만 사용하도록 설계하는 것이 좋다***

* **State**
    * State는 리액트 컴포넌트의 상태를 의미한다
    * 상태의 의미는 정상인지 비정상인지가 아니라 컴포넌트의 데이터를 의미한다
    * 정확히는 컴포넌트의 변경 가능한 데이터를 의미
    * State가 변하면 다시 렌더링이 되기 때문에 렌더링과 관련된 값만 state에 포함시켜야 한다

* **State의 특징**
    * 리액트만의 특별한 형태가 아닌 단지 자바스크립트 객체일 뿐이다.

* **생명주기**
    * 생명주기는 컴포넌트의 생성, 사용, 종료 시점을 나타내는 것이다
    * constructor가 싱행 되면서 컴포넌트 생성
    * 생성 직후 componentDidMount()함수 호출
    * 컴포넌트가 소멸하기 전까지 여러 번 렌더링한다.
    * 렌더링은 props, setState(), forceUpdate()에 의해 상태가 변경되면 이루어진다.
    * 렌더링이 끝나면 componentDinUpdate()함수 호출
    * 마지막으로 컴포넌트가 언마운트 되면 compomentWillUnmount()할수 호출

## 2024-03-27
### JSX의 역할
* JSX는 내부적으로 XML/HTML 코드를 자바스크립트로 변환
* Reaxt가 createElement함수를 사용 하여 자동으로 자바스크립트로 변환
* 만일 JS로 작업할 경우 직접 createElement함수를 사용해야 함
* JSX는 가독성을 높여 주는 역할을 한다.  

### JSX의 장점
* 코드가 간결해 짐
* 가독성 향상
* Inhection Attack을 방어함으로써 보안성 향상

### JSX의 사용법
* 모든 자바스크립트 문법을 지원
* 자바스크립트 문법에 XML과 HTML을 섞어서 사용
* 만일 html이나 xml에 자바스크립트 코드를 사용하고 싶으면 {}괄호를 사용
* 만일 태그의 속성값을 넣고 싶다  
    -> 큰따음표 사이에 문자열을 넣거나 중괄호 사이에 자바스크리브 코드를 넣는다
    
### 엘리먼트
* **엘리먼트의 정의**
    * 엘리먼트 = 리액트 앱을 구성하는 요소
    * 공식 페이지에는 "앨리먼트는 리액트 앱의 가장 작은 빌딩 블록들" 이라고 설명
    * 웹 사이트의경우는 DOM 엘리먼트이며, HTML의 요소를 의미  

* **리액트 엘리먼트와 DOM 엘리먼트의 차이**
    * 리액트 엘리먼트는 Virtual DOM의 형태를 취하고 있다
    * DOM 엘리먼트는 페이지의 모든 정보를 갖고 있어서 무겁다
    * 반면 리액트 엘리먼트는 변화한 부분만 갖고 있어서 가볍다  

* **엘리먼트의 생김새**
    * 리액트 엘리먼트는 자바스크립트 객체의 형태로 존재
    * 컴포넌트, 속성, 및 내부의 모든 children을 포함하는 일반 JS객체
    * 이 객체는 마음대로 변경할 수 없는 불변성을 갖고 있다

* **엘리먼트의 특징**
    * 리액트 엘리먼트의 가장 큰 특징 = 불변성 즉, 한 번 생성된 엘리먼트의 children이나 속성을 바꿀 수 없다.

* **엘리먼트 렌더링하기**
    * 다음 HTML코드는 id 값이 root인 div 태그로 단순하지만 이랙트에 필수로 들어가는 아주 중요한 코드이다.  
    * 이 div태그안에 리액트 엘리먼트가 렌더링 되먀, 이것을 Root DOM node라고 한다.
    ```
    <div id = "root"></div>
    ```

* **엘리먼트 업데이트하기**
    * 함수 tick()을 정의하고 현재 시간을 포함한 element를 생성해서 root div에 렌더링한다.
    * setInterval()함수를 이용해 위에서 정의한 tick을 1초에 한번씩 호출
    * 결국 1초에 한번씩 element를 새로 만들고 그것을 교체하는 것이다.
    * 다음 코드를 실행하고, 크롬 개발자도구에서 확인해 보면 ㅣ간 부분만 업데이트 되는 것을 확인 가능함
    ```
    function tick(){
        const element = (
            <div>
                <h1>안녕, 리액트!</h1>
                <h2>현재 시간: {new Date().toLocalTimeString()}</h2>
            </div>
        );

        ReactDOM.render(elemetn, document.getElementById('root'));
    }

    setIntervak(tick, 1000);
    ```
* **컴포넌트**
    * 리액트는 컴포넌트 기반의 구조를 같습니다.
    * 컴포넌트 구조라는 것은 작은 컴포넌트가 모여 큰 컴포넌트를 구성하고, 다시 이런 컴포넌트들이 모여서 전체 페이지를 구성한가는 것을 의미
    * 컴포넌트 재사용이 가능하기 때문에 전체 코드의 양을 줄일 수 있어 개발 시간과 유지 보수 비용도 줄일 수 있다
    * 컴포넌트는 자바스크립트 함수와 입력과 출력이 있다는 면에서는 유사
    * 다만 입력은 Props가 담당하고, 출력은 리액트 엘리먼트의 형태로 출력
    * 엘리먼트를 필요한 만큼 만들어 사용한다는 면에서는 객체 지향의 개념과 비슷

* **Props**
    1. Props의 개념
        * props는 prop의 준말
        * 이 props가 컴포넌트의 속성
        * 컴포넌트에 어떤 속성, props를 넣느냐에 따라서 속성이 다른 엘리먼트가 출력
        * props는 컴포넌트에 전달 할 다양한 정보를 담고 있는 자바스크립트 객체

    2. Props의 특징
        * 읽기 전용, 변경할 수 없다는 의미
        * 속성이 다른 엘리먼트를 생성하려면 새로운 props를 컴포넌트에 전달하면 된다
    * ***모든 리액트 커포넌트는 props를 직접 바꿀 수 없고, 같은 props에 대해서는 항상 같은 결과를 보여준다***
* Pure 함수 vs Impure함수
    * Pure함수는 인수로 받은 정보가 함수 내부에서도 변하지 않는 함수
    * Impure함수는 인수로 받은 정보가 함수 내에서 변하는 함수
        
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


## 기타
npm uninstall -g create-react-app  
npm install -g create-react-app  
npx create-react-app 프로젝트이름  
* node 재설치  
    npm cache clean --force  
    npm install -g node@latest