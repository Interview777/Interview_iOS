# 3 주차 대표 문제

<details>
<summary>MVC의 단점이나 한계에 대해 설명하시오</summary>
<div markdown="1">
    MVC는 Model과 View와 Controller가 서로 상호작용하며 앱을 구성하는 아키텍쳐이지만, 결국 Controller가 앱의 거의 대부분의 로직을 담당하게 되면서 Massive View Controller라는 이명에 걸맞게 컨트롤러가 너무 방대해지는 문제가 있습니다. 이는 앱의 로직이 복잡해질수록, 뷰의 구성이 복잡해질수록 더욱 심해집니다. 그리고 구조상 View와 Model을 Controller가 모두 알고 있게 되기에 의존성이 Controller에 집중되면서 위와 같은 문제가 더욱 심해진다 생각합니다.
이를 해결하기 위해 현재 다양한 아키텍쳐들이 등장하였고, 이 아키텍쳐들을 통해 Controller의 부담을 줄이고 복잡도를 줄여주고 있습니다.
</div>
</details>

<details>
<summary>Swift내에서 상속을 받은 클래스의 init의 절차를 설명해주세요.</summary>
<div markdown="1">
자식 클래스 내에 편의 생성자로 생성되는 절차를 기준으로 말씀드리겠습니다. 편의 생성자는 자기 자신의 지정 생성자를 호출하여서 자신의 프로퍼티들을 초기화 하게 됩니다. 이 지정 생성자는 다시 상속하고 있는 클래스의 생성자를 호출해야만 합니다. 그 이유는 초기화를 하는 과정에서 부모 클래스가 생성되지 않는 것은 위험하다고 판단하기 때문에 swift에서는 부모 클래스의 생성자를 무조건 호출하도록 합니다.
    
자기 자신의 프로퍼티를 먼저 초기화한 후 super의 이니셜라이저를 호출하여 부모 클래스를 초기화한다 그런 다음 2차 초기화프로세스를 통해서 자기 자신을 한번 더 재설정할 기회가 주어진다.
</div>
</details>

<details>
<summary>lazy stored properties 는 무엇이고, 사용하면 어떤 이점이 있습니까?</summary>
<div markdown="1">
   지연 저장 프로퍼티(lazy stored properties)는 호출이 있어야 값을 초기화하는 저장 프로퍼티 입니다. 지연 저장 프로퍼티를 사용하면 필요할 때 값을 초기화하기 때문에 공간 낭비를 줄일 수 있고 복잡한 클래스나 구조체를 생성할 때 불필요한 프로퍼티의 초기화를 방지해서 성능 저하를 방지할 수 있습니다.
    
</div>
</details>

<details>
<summary>싱글턴 패턴이 무엇이며 어떠한 장단점이 있나요?</summary>
<div markdown="1">
    a. 싱글턴은 클래스에 인스턴스가 하나만 있도록 하면서 이인스턴스에 대한 전역 접근(액세스) 지점을 제공하는 생성 디자인 패턴이다.

a. 장점은 하나의 인스턴스를 기반으로 해당 인스턴스를 다른 모듈들이 공유하여 사용하기 때문에 인스턴스 비용 감소하고 하나의 인스턴스를 전역적으로 사용하기 때문에 데이터를 공유하기 쉽고 인스턴스가 하나만 존재해야 하는 경우 사용하기 좋다.
a. 단점은 유닛테스트가 힘들고 인스턴스끼리 결합도가 높아진다.
</div>
</details>

# 3 주차 문제

## wonbi
1. **KVO에서 `@objc dynamic`이 의미하는 것은 무엇인지 설명하시오**
    a. `@objc dynamic`는 변화를 관찰하려는 프로퍼티에 어노테이팅 해주는 접두사입니다. 이 접두사를 어노테이션 해줌으로써, 프로퍼티를 오브젝트C 런타임에 노출시키고, Message Dispatch사용하도록 합니다.
    
2. **NotificationCenter을 활용하는 방법중 하나를 설명하시오**
    a. global queue에서 비동기적으로 실행되는 어떠한 로직이 있을 때, 그 로직이 끝났다는 것을 알리는 용도로 사용할 수 있습니다. 이는 컴파일단에서 언제 이 로직이 끝나는지 알 수 없으므로, NotificationCenter를 사용하는 것이 하나의 방법이 될 수 있습니다.
    애플이 기본적으로 제공하는 Notification을 활용할 때 사용할 수 있습니다. 예를들어, 키보드가 등장할 것이다. 앱이 백그라운드로 진입하였다. 등의 상황에서 NotificationCenter를 활용하면 특정한 로직을 실행시키도록 활용할 수 있습니다.
    
3. **지정 이니셜라이져와 편의 이니셜라이저의 차이점을 설명하시오**
    a. 지정 이니셜라이저는 클래스의 기둥과 같은 주요 이니셜라이저로, 클래스에 1개 이상 존재해야 하는 이니셜라이저 입니다. 
    편의 이니셜라이저는 말 그대로 이니셜라이저의 역할에 도움을 주는 역할을 하는 이니셜라이저입니다. 스스로 모든 값을 초기화 할 수 는 없기 때문에 지정 이니셜라이저를 내부에서 반드시 호출해주어야 합니다.
    편의 이니셜라이저는 지정 이니셜라이저의 전달인자가 많아 일일히 입력하기 힘들거나, 특정 목적을 위해 사용합니다. 예를들어, 객체를 초기화 할때, 특정 전달인자들의 상황에 따라 기본값이 필요한 경우에 이 편의 이니셜라이저를 통해 해당 전달인자들에 기본값을 주고, 나머지 전달인자들을 지정 이니셜라이저를 통해 초기화 하는 방법으로 활용할 수 있습니다.
    
4. **MVC의 단점이나 한계에 대해 설명하시오**
    a. MVC는 Model과 View와 Controller가 서로 상호작용하며 앱을 구성하는 아키텍쳐이지만, 결국 Controller가 앱의 거의 대부분의 로직을 담당하게 되면서 Massive View Controller라는 이명에 걸맞게 컨트롤러가 너무 방대해지는 문제가 있습니다. 이는 앱의 로직이 복잡해질수록, 뷰의 구성이 복잡해질수록 더욱 심해집니다. 그리고 구조상 View와 Model을 Controller가 모두 알고 있게 되기에 의존성이 Controller에 집중되면서 위와 같은 문제가 더욱 심해진다 생각합니다.
    이를 해결하기 위해 현재 다양한 아키텍쳐들이 등장하였고, 이 아키텍쳐들을 통해 Controller의 부담을 줄이고 복잡도를 줄여주고 있습니다.
    
5. **디자인 패턴의 의도나 목적에 따라 분류된 세가지 패턴을 설명하시오.**
    a. 생성 패턴, 구조 패턴, 행동 패턴 세가지로 나눌 수 있습니다.
    생성 패턴은 코드의 재사용성과 유연성을 올리기 위해 객체 생성 메커니즘을 제공하는 패턴입니다.
    구조 패턴은 구조를 유연하고 효율적으로 관리하기 위해 객체와 클래스를 더 큰 구조로 조합하는 방법을 제공하는 패턴입니다.
    행동 패턴은 객체와 객체간의 효과적인 의사소통과 책임 할당을 위한 벙법을 제공하는 패턴입니다.
    
6. **소프트웨어 아키텍처와 디자인 패턴의 차이점**
    a. 소프트웨어 아키텍처는 프로그램 내에서 큰 구조로 구성되어 다른 구성 요소들을 관리하는 역할을 합니다. 반면에 디자인 패턴은 특정 유형의 문제를 해결하는 방법으로 소프트웨어 아키텍처보다는 조금 더 좁은 개념에 포함됩니다.

## 준호
1. **디자인 패턴은 무엇입니까?**
   a. 프로그램 개발에서 자주 발생하는 문제를 해결하기 위해 사용하는 형식화되고 재사용 가능한 방법입니다.
   
2. **소프트웨어 아키텍처는 무엇입니까?**
   a. 소프트웨어의 구성요소들 사이의 유기적 관계를 정의하고 설계하기 위한 구조입니다.
   
3. **기존 MVC와 애플의 Cocoa MVC의 차이점은 무엇입니까?**
   a. 기존 MVC 패턴과 달리 Cocoa MVC는 View와 Model이 직접 통신하지 않고 Controller를 통해서 Model의 상태변화를 View에 전달합니다.
   
4. **lazy stored properties 는 무엇이고, 사용하면 어떤 이점이 있습니까?**
   a. 지연 저장 프로퍼티(lazy stored properties)는 호출이 있어야 값을 초기화하는 저장 프로퍼티 입니다. 지연 저장 프로퍼티를 사용하면 필요할 때 값을 초기화하기 때문에 공간 낭비를 줄일 수 있고 복잡한 클래스나 구조체를 생성할 때 불필요한 프로퍼티의 초기화를 방지해서 성능 저하를 방지할 수 있습니다.
  
5. **Key-value observing은 무엇입니까?**
   a. KVO는 다른 객체의 변경 사항을 객체에 알리는 데 사용하는 코코아 프로그래밍 패턴입니다. NSObject를 상속한 클래스에서만 KVO를 사용할 수 있습니다.
   
6. **Notification Center를 사용하여 데이터를 전달하는 방법을 설명하세요.**
   a. 데이터를 받을 곳에서 NotificationCenter 객체의 `addObserver` 메서드를 통해 자신을 옵저버로 추가한 뒤 데이터를 보낼 곳에서 NotificationCenter 객체의 `post` 메서드를 호출하여 데이터를 담은 Notification을 보냅니다.

## 하모
1. **KVO는 무엇이며 Property Observer와의 차이는 무엇인가?**
    a. 다른 객체의 프로퍼티를 옵저빙할 수 있는 메커니즘이다. KVO를 통해서 model과 view처럼 논리적으로 분리된 파트끼리 소통할 때 유용하게 사용할 수 있다. NSObject를 상속받는 클래스에서만 사용할 수 있다는 단점이 존재한다.

    a. Property Observer는 객체 자신의 프로퍼티의 변화를 옵저빙할 수 있고 다른 객체의 프로퍼티를 옵저빙하지는 못한다. 반면에 KVO는 다른 객체에 있는 프로퍼티의 변화를 옵저빙할 수 있다.

2. **NotificationCenter은 무엇이며 장점과 단점은 무엇인가?**

    a. 등록된 관찰자에게 정보를 브로드캐스트할 수 있는 알림 디스패치 메커니즘이다.

    a. 간단하게 이벤트/동작을 구현할 수 있고 다수의 객체에게 동시에 노티를 보낼 수 있다. 단점으로는 무분별하게 사용했을 때 디버깅이 어려워질 수 있다.

3. **Default Initializer와 Memberwise Initializer에 대해서 설명해주세요**

    a. Swift는 모든 프로퍼티에 기본값을 할당하고 초기화 구문을 정의하지 않은 구조체 또는 클래스에 default initializer를 제공한다.

    a. 구조체 타입은 initializer를 정의하지 않으면 자동으로 memberwise initializer를 제공 받는다. memberwise initializer를 호출할 때 기본값을 가지는 프로퍼티는 생략할 수 있다.

4. **애플이 이야기하는 MVC 구조에서 각각의 역할이 무엇이며 어떤 장점이 있을까요?**

    a. Model은 데이터를 다루는 부분을 담당한다.
    a. View은 화면에 보여지는 시각적인 UI를 담당한다.
    a. Controller는 뷰와 모델 사이의 중개자 역할을 한다. 상호작용을 관리하고 View에 들어온 사용자의 입력을 토대로 Model을 변경하고, 변경된 Model로 View를 갱신하는 역할과 어플리케이션에 대한 설정, 조정 작업을 수행하고 다른 객체의 수명 주기를 관리

    a.분리를 했을 때 재사용이 가능해지고 확장성이 좋고, 서로 결합도를 떨어트리기 좋다.

5. **아키텍처나 디자인 패턴은 왜 필요할까요??**

    a.자주 발생하는 문제들에 대해 정형화된 해결 방법을 제공함으로써, 향후 비슷한 유형의 문제가 발생했을 때 해당 패턴을 응용하여 문제를 해결할 수 있다.
    a.협업 시 효율성을 높여주고, 의사소통을 보다 원활하게 해준다.
    a.아키텍처나 디자인 패턴으로 구현함으로 특정 기능을 유지보수할 때 유연하게 가능하다.

6. **싱글턴 패턴이 무엇이며 어떠한 장단점이 있나요?**

    a. 싱글턴은 클래스에 인스턴스가 하나만 있도록 하면서 이인스턴스에 대한 전역 접근(액세스) 지점을 제공하는 생성 디자인 패턴이다.
    a. 장점은 하나의 인스턴스를 기반으로 해당 인스턴스를 다른 모듈들이 공유하여 사용하기 때문에 인스턴스 비용 감소하고 하나의 인스턴스를 전역적으로 사용하기 때문에 데이터를 공유하기 쉽고 인스턴스가 하나만 존재해야 하는 경우 사용하기 좋다.
    a. 단점은 유닛테스트가 힘들고 인스턴스끼리 결합도가 높아진다.

## 미니
1. **MVC 패턴에서 각각의 역할은 무엇이고, 이것이 코드에서 어떻게 나타나는 지 설명하시오.**
    a. Model은 앱이 가지는 데이터를 말합니다. 이는 코드 상에서 저희가 뷰에 보여줄 데이터의 커스텀 타입으로 나타나게 됩니다. 뷰는 데이터를 보여주는 역할을 가지고 있습니다. Controller는 모델의 변경사항을 어떻게 뷰에 보여주게 할 것인지에 대한 역할을 가지게 됩니다. 이는 코드 상에서 UIViewController 타입을 상속 받아서 구현한 커스텀한 ViewController로 표현되게 됩니다. 또한, 이 안에는 View도 함께 나타나게 됩니다.


2. **iOS의 MVC 패턴의 단점을 설명해주세요.**
    a. View와 Controller가 한개의 클래스에서 함께 표현이 되게 됩니다. 한개의 클래스가 뷰의 역할과 Controller의 역할을 모두 함께 하는 것을 의미하게 되며, 이는 Controller가 View의 life Cycle도 관여를 하는 것이 됩니다. 이로 인해서 View와 Controller가 강하게 연결되어 있어서 테스트가 어렵습니다.


3. **모델은 다른 컴포넌트들을 알면 안되는데 Controller는 모델의 변화를 어떻게 감지 할 수 있을까요?**
    a. Apple이 기본적으로 제공하는 KVO, NotificationCenter와 같은 Observer 패턴을 활용하거나, Delegate 패턴을 활용할 수도 있습니다. 또한, 클로저를 이용한 CompletionHandler를 활용하는 방법이 있습니다.


4. **KVO는 무엇인가요? 프로퍼티 감시자와 다른 점이 무엇인가요?**
    a. KVO는 Key-Value Observing이라고 하며, 다른 오브젝트의 프로퍼티 속성이 변경되었을 때, 오브젝트에서 변경사항을 알 수 있게 해주는 것입니다. 프로퍼티 감시자는 타입 내부의 값에 대한 관찰만 가능하지만, KVO는 다른 오브젝트의 속성을 감지할 수 있습니다.


5. **Swift내에서 상속을 받은 클래스의 init의 절차를 설명해주세요.**
    a. 자식 클래스 내에 편의 생성자로 생성되는 절차를 기준으로 말씀드리겠습니다. 편의 생성자는 자기 자신의 지정 생성자를 호출하여서 자신의 프로퍼티들을 초기화 하게 됩니다. 이 지정 생성자는 다시 상속하고 있는 클래스의 생성자를 호출해야만 합니다. 그 이유는 초기화를 하는 과정에서 부모 클래스가 생성되지 않는 것은 위험하다고 판단하기 때문에 swift에서는 부모 클래스의 생성자를 무조건 호출하도록 합니다.


6. **NotificationCenter를 활용하는 과정을 설명해주세요.**
    a. 프로퍼티가 변경될 때 알림을 등록할 객체가 노티피케이션 센터에 알림을 등록 합니다. 그런 후, 노티피케이션 센터는 각 뷰 컨트롤러에게 해당 알림이 등록 된 것을 전파하게 됩니다. 해당 값을 구독하고 있는 객체는 해당 알림을 받아서 처리하게 됩니다.
