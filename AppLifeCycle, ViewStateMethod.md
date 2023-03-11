# 대표 문제
<details>
    <summary>scene이 무엇인가요??</summary>
    <div markdown="1">
a. scene은 기기에서 실행되는 앱 UI의 한 인스턴스를 나타내고 사용자는 각 앱에 대해 여러 scene을 만들고 별도로 표시하거나 숨길 수 있습니다. 각 scene에는 고유한 life cycle이 있기 때문에 각각 다른 상태에 있을 수 있습니다.
    </div>
</details>

<details>
    <summary>App의 suspend 상태는 무엇인가요?</summary>
    <div markdown="1">
a. 백그라운드에서 추가적인 작업을 하지 않은 상태입니다. 앱이 background 상태에서 추가적인 작업을 하지 않으면 곧바로 suspended 상태로 진입합니다. 앱을 다시 실행할 경우 빠른 실행을 위해 메모리에만 올라가 있습니다. 하지만 메모리가 부족한 상황이 되면 iOS는 suspended 상태에 있는 앱들을 메모리에서 해제시켜서 메모리를 확보합니다.
    </div>
</details>

<details>
    <summary>App Delegate와 Scene Delegate의 각각의 역할은 무엇일까요?</summary>
    <div markdown="1">
a. scene delegate는 UI의 life cycle을 관리하는 역할을 하고 app delegate는 전체적인 앱의 수명을 관리합니다. 
a. 자세히 알아보면 app delegate는 앱의 중앙 데이터 구조를 초기화하고 앱의 scene을 구성하고 메모리 부족 경고, 다운로드 완료 알림 등 앱 외부에서 발생하는 알림에 응답하고 APNS 서비스 등 출시 시 필요한 서비스를 등록하는 데 사용합니다.
a. scene delegate는 scene이 foreground로 진입하여 활성화될 때와 background로 진입할 때를 포함하여 scene에 영향을 미치는 상태 전환에 응답하는 메서드를 정의합니다.
    </div>
</details>

<details>
    <summary>iOS 13 이전과 이후의 AppDelegate는 어떤 것이 변경되었나요?</summary>
    <div markdown="1">
a. 13 이후에는 앱의 가장 중요한 데이터 구조를 초기화 하고, 앱의 Scene에 대한 환경설정을 하게 됩니다. 또한, 앱 자체를 타겟하는 이벤트에 대응하게 됩니다.
    </div>
</details>

<details>
    <summary>loadView 메서드와 viewDidLoad 메서드의 차이는 무엇인가요?</summary>
    <div markdown="1">

a. loadView 메서드는 뷰가 로드를 시작하면 호출되고 viewDidLoad 메서드는 뷰가 메모리에 로드된 후 호출됩니다. loadView 메서드는 스토리보드를 사용하지 않고 뷰를 직접 생성할 때 재정의하여 사용합니다.
    </div>
</details>

Wonbi
1. **viewWillAppear와 viewWillDisappear에서 무엇을 하면 좋을지 설명하시오.**
    a. viewWillAppear는 뷰가 화면에 보이기 직전에 불리는 메서드로 인터페이스에 대한 최종 업데이트를 수행해야 합니다. 예를들어 UI애니메이션 시작하기, 미디어파일 자동재생시작, 게임이나 몰입형 컨텐츠의 그래픽 표시시작하기 등입니다.
    a. viewWillDisappear는 뷰가 화면에서 사라지기 직전에 불리는 메서드로 사용자에게 입력받았던 데이터나 변경 사항을 커밋하거나, 뷰의 first responder 상태를 포기하는 등의 작업을 수행해야 합니다.
2. **UIView의 layoutSubviews가 viewWillAppear보다 나중에 호출되는 이유를 설명하시오.**
    a. layoutSubviews 메서드는 서브뷰를 배치하는 메서드이므로, 서브뷰를 배치하기 위해 먼저 부모뷰가 화면에 배치되어있어야 서브뷰를 배치할 수 있기 때문에 viewWillAppear메서드가 호출이 끝나고 뷰가 화면에 배치된 후 호출됩니다.
3. **앱이 foreground에 있을 때와 background에 있을 때 어떤 특징이 있는지 설명하시오.**
    a. Foreground는 앱이 사용자에게 보여지고 있는 상태로 메모리 및 시스템 리소스에 높은 우선 순위를 가지고 있습니다.
    a. background 는 앱이 백그라운드에 있지만 여전히 실행되고 있는 상태를 말합니다. 대부분의 상황에서 이벤트에 응답할 수 없지만, 특수한 몇몇의 경우에는 관련된 이벤트에 대한 응답을 위한 자원을 부여합니다. 예를들어 VoIP, 위치 서비스, AirPlay, 외부 악세서리와 통신, APNs 등이 있습니다.
4. **UIApplication의 State의 active와 inactive의 차이점에 대해 설명하시오.**
    a. 두 상태 모두 앱이 포어그라운드에서 실행되고 있는 상태이며, active는 앱이 사용자의 이벤트를 받는 상태를 말하고, inactive는 사용자의 이벤트를 받지 않는 상태를 의미합니다. 
5. **사용자가 앱을 실행하여 포어그라운드에 진입하는 과정을 설명하시오.**
    a. 앱이 터치되어 실행되면, 런치 과정에서 씬 델리게이트의 `sceneWillEnterForeground(_:)` 메서드를 실행하여 포어그라운드로 전환하기 전 인액티브 상태로 시작합니다. 이후 필요한 메서드들을 실행한 후 `sceneDidBecomeActive(_:)` 메서드를 실행하여 액티브 상태로 전환합니다.

준호
1. **loadView 메서드와 viewDidLoad 메서드의 차이는 무엇인가요?**
   a. loadView 메서드는 뷰가 로드를 시작하면 호출되고 viewDidLoad 메서드는 뷰가 메모리에 로드된 후 호출됩니다. loadView 메서드는 스토리보드를 사용하지 않고 뷰를 직접 생성할 때 재정의하여 사용합니다.
2. **뷰의 상태 변화 메서드를 순서대로 말하세요.**
   a. viewDidLoad, viewWillAppear, viewDidAppear, viewWillDisappear, viewDidDisappear
3. **Scene은 무엇입니까?**
   a. multiple winodw를 지원하면서 생겨난 개념으로 Scene 을 활용하여 한 개의 앱에서 여러 화면을 사용할 수 있습니다.
4. **Background 상태와 Suspended 상태의 차이는 무엇인가요?**
   a. Background 상태에서 추가적인 작업을 하지 않으면 suspended 상태로 넘어갑니다. background 상태에서 동작하는 코드를 추가하면 suspended 상태로 넘어가지 않고 background 상태를 유지합니다.
5. **iOS 13 이후 App Delegate와 Scene Delegate의 역할에 대해서 설명하세요.**
   a. App Delegate는 새로운 Scene Session이 생성되거나 버려질 때 알리는 역할을 맡습니다. Scene Delegate는 UI 상태 변화를 알려주는 역할을 맡습니다.


미니
1. **View State Method에서 loadView와 ViewDidLoad는 어떤 역할을 하고 어떤 차이가 있나요?**
    a. loadView는 뷰를 만드는 메서드입니다. 하지만, ViewDidLoad는 뷰가 메모리에 메모리에 로드된 후에 불리게 되는 차이가 있습니다.
2. **iOS 13 이전과 이후의 AppDelegate는 어떤 것이 변경되었나요?**
    a. 13 이후에는 앱의 가장 중요한 데이터 구조를 초기화 하고, 앱의 Scene에 대한 환경설정을 하게 됩니다.  또한, 앱 자체를 타겟하는 이벤트에 대응하게 됩니다.
3. **앱이 In-Active 상태가 되는 시나리오를 설명하시오.**
    a. 앱이 최초로 실행되는 경우, not-running에서 인엑티브 상태를 진입 후, 액티브 상태가 됩니다. 또한, 앱이 액티브 상태에서 백그라운드로 전환되는 과정에서, 인액티브 상태를 거치게 됩니다. 이에 대한 예시로, 포그라운드 앱 스위처를 작동시킨 경우가 있습니다. 마지막으로, 백그라운드에서 액티브 상태로 전환되는 과정에서 인엑티브 상태를 거치게 됩니다.
4. **SceneDidDisconnect는 언제 호출 될까요?**
    a. Scene이 백그라운드로 들어간 후, 시스템이 자원을 확보하기 위해서 disconnect를 합니다. 이 메서드는 앱을 종료 시키는 것과는 다르고, 단순히 session이 끊어지는 것입니다. 
5. **ViewDidLoad 메서드 이후에 일어나는 Method는 어떤 것들이 있고, 각각 어떤 순서로 일어나는 지 말씀해주세요.**
    a. ViewWillAppear는 컨트롤러의 화면이 올라오고 난 후, 뷰가 화면에 나타나기 직전에 호출됩니다.  그 후, ViewDidAppear 메서드가 호출되며, 이는 View가 데이터와 함께  완전히 화면에 나타난 후 호출됩니다.화면이 사라지기 전에는 ViewWillDisAppear 메서드가 호출됩니다. 화면이 사라질 때, ViewDidDisAppear 메서드가 호출됩니다.

쿄
1. **메모리에 view를 올리는 View State Method는 무엇인가요?**
    a. LoadView()입니다.
    loadView()가 view를 만들고, 메모리에 올리는 역할을 합니다.
2. **그러면 viewDidLoad()의 역할은 무엇인가요?**
    a.`viewDidLoad`는 이 뷰가 모두 생성되고 메모리에 생성된 후에 호출되는 메서드입니다. 시스템에 의해 자동으로 호출되며 처음 한 번만 실행해야 하는 초기화 코드가 있을 경우 작성합니다.
3. **App의 모든 상태를 말해주세요.**
    a. Not Running, Inactive, Active, Background, Suspended 상태가 있습니다.
4. **App의 suspend 상태는 무엇인가요?**
    a. 백그라운드에서 추가적인 작업을 하지 않은 상태입니다. 앱이 background 상태에서 추가적인 작업을 하지 않으면 곧바로 suspended 상태로 진입합니다. 앱을 다시 실행할 경우 빠른 실행을 위해 메모리에만 올라가 있습니다. 하지만 메모리가 부족한 상황이 되면 iOS는 suspended 상태에 있는 앱들을 메모리에서 해제시켜서 메모리를 확보합니다.
    
5. **AppDelegate와 SceneDelegate에 대해서 설명해주세요.**
    a. App Delegate는 앱의 프로세스 Life cycle 담당하고, Session Lifecycle  담당합니다. 그리고 SceneDelegate는 UI의 상태를 알 수 있는 UI Lifecycle을 담당합니다.
    
하모
1. **scene이 무엇인가요??**
    a. scene은 기기에서 실행되는 앱 UI의 한 인스턴스를 나타내고 사용자는 각 앱에 대해 여러 scene을 만들고 별도로 표시하거나 숨길 수 있습니다. 각 scene에는 고유한 life cycle이 있기 때문에 각각 다른 상태에 있을 수 있습니다.
2. **iOS 13부터 UIKit은 앱의 상태가 변경되었을 때 어떻게 알려주나요??**
    a. UISceneDelegate 객체를 사용하여 scene 기반 앱의 life cycle 이벤트에 응답합니다.
3. loadView 메서드는 언제 호출되며 어떤 역할을 하나요??
    a. 뷰 프로퍼티가 요청되었지만 현재 nil일 때 이 메서드를 호출하고 컨트롤러가 관리하는 뷰를 만드는 역할을 합니다. 뷰를 수동으로 생성하기 위해 이 메서드를 재정의할 수 있습니다. 뷰 계층 구조의 루트 뷰를 뷰 프로퍼티에 할당합니다.
4. **App Delegate와 Scene Delegate의 각각의 역할은 무엇일까요?**
    a. scene delegate는 UI의 life cycle을 관리하는 역할을 하고 app delegate는 전체적인 앱의 수명을 관리합니다. 
    a. 자세히 알아보면 app delegate는 앱의 중앙 데이터 구조를 초기화하고 앱의 scene을 구성하고 메모리 부족 경고, 다운로드 완료 알림 등 앱 외부에서 발생하는 알림에 응답하고 APNS 서비스 등 출시 시 필요한 서비스를 등록하는 데 사용합니다.
    a. scene delegate는 scene이 foreground로 진입하여 활성화될 때와 background로 진입할 때를 포함하여 scene에 영향을 미치는 상태 전환에 응답하는 메서드를 정의합니다.
5. **앱의 상태가 Background로 지속되기 위한 요건은 무엇인가요??**
    a. 백그라운드 상태이지만, 아직 실행되어야 할 이유가 남았을 때입니다. 예를 들어 오디오, 위치, 다운로드, 알림, 블루투스를 사용중일 때를 말합니다.
