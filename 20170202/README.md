##20170202#

별그리기 예제 내용.  
1.위에서 1,2,3
2.위에서 3,2,1
3.위에서 오른쪽 끝부터 1,2,3
4,위에서 가운데정렬로. 1,2,3

[iOS구조 파악]

앱의 구조 : MVC. 
· 모델, 컨트롤러, 뷰 
· 이벤트 루프 : Ex. 사용자의 터치 …와 같은 것을 받아들여서 계속 돌아가는 것…
· 뷰 : 기본적으로 앱의 기본적 윈도우는 검은색…뷰를 이 윈도우 위에 올려서 앱의 화면을 띄워주는 것…
· 보통 뷰 컨트롤러가 뷰를 하나씩 관리해줌…따라서 일반적 앱들은 한 화면에 뷰 컨트롤러가 하나가 들어감
Ex. 넥스트 버튼 누르면 화면전환 되는 것은 뷰 컨트롤러가 전환되는 것…
물론 나중에 가면 한 화면에 뷰 컨트로러가 두개씩 들어가긴 하나…기본적으론 한 화면에 뷰 컨트롤러가 하나…
· 앱 델리게이트 : 앱의 전반적 상태에 대한 정보를 받음
· 데이터 오브젝트 : 데이터를 앱 델리게이트, 뷰 컨트롤러로 보냄
앱 델리게이트와 뷰. 컨트롤러는 각각 UI윈도우, 뷰-UI오브젝트로 보내줌

화면구조 
“보통 한장의 화면 하나하나 마다 뷰 컨트롤러가 있다”

[UI Base Guide]

Resolutions 
· 픽셀 : 실제 이미지 사이즈
“모니터 화면, 이미지의 점 하나하나” 
· 포인트 : 화면에 표시되는 이미지 사이즈
“iOS는 픽셀을 한 번 감싸서 픽셀이 아닌, 포인트라는 [화면에 표시되는 점 하나] 라는 개념을 사용함”
즉 500 x 500 픽셀의 이미지가 iOS에 들어가면 그건 500 x 500 포인트의 이미지가 아니다…즉 픽셀과 포인트는 1:1 매칭이 안된다…이유? 레티나 디스플레이 
1포인트에는 총 4픽셀이 들어감…
디자이너에게 이미지에 관해 이야기 할 땐 픽셀로 이야기를 해야 하고, 
개발자는 코딩할 때 포인트로 다뤄야 함

아이폰5 : 320포인트 = 640 픽셀 / 568 포인트 = 1188 픽셀
아이폰6 : 375포인트 = 750픽셀 / 667포인트 = 1344 픽셀
아이폰6+ : 414포인트= 1242픽셀 / 736포인트 = 2208 픽셀 (6+는 3배)

좌표계 
· 뷰 기준으로 좌측상단의 좌표는 0,0임 
· 우측으로 갈 수록 x좌표 증가
· 하단으로 갈 수록 y좌표 증가
단 코어그래픽스, iOS게임 프레임워크, openGL의 좌표계는 수학책에서 보던 그래프와 동일함
혼용하면 좌표계가 뒤틀리게 됨

좌표계의 뷰 
· 뷰의 위치는 상대적으로 상위뷰를 기준으로 위치를 잡는다
· 뷰는 포토샵처럼 레이어 구조로 쌓을 수 있음 + 뷰 간 상하관계(계층관계)를 만들 수 있음
---- >계층관계에 따라서 위치를 정하게 됨…
Ex. 자식 뷰(서브 뷰)를 설정하면 부모 뷰 위로 올라감…부모 뷰를 움직이면 서브 뷰도 움직임……서브 뷰의 서브 뷰도 움직임…”귀속 되어”있으므로…
· 좌표 또한 상위 뷰를 기준으로 판단해야 한다…”좌표는 부모, 자식간 관계에 따라 상대적이다”
Ex. 서브 뷰의 좌표 : 10,20 / 서브 뷰는 백그라운드의 자식 뷰 라면, 
== 버튼 ui가 서브 뷰의 자식이라면 좌표는 5,40 
== 버튼 ui가 메인 뷰의 자식이라면 좌표는 15,60

[View]

프레임워크란
· 애플리케이션프레임워크는 프로그래밍에서 특정 운영체제를 위한 음용프로그램 표준 구조를 구현하는 클래스와 라이브러리의 모임
· 재사용 가능한 수많은 코드를 프레임워크로 통합함으로써 개발자가 새로운 애플리케이션을 위한 표준 코드를 다시 작성하지 않아고 같이 사용
· 객체지향 프로그래밍 기법이 사용되고 있는 응용 프로그램 고유의 클래스가 프레임워크의 기존 클래스를 상속할 수 있음
· 프레임워크는 페이스북 프레임워크, 코어그래픽스 프레임워크 등 원하는 것을 다운 받아서 쓰는 것이 가능함

UIKit Framework 
· 코코아터치 프레임워크에 추가된 UI관련 기능의 클래스가 모여있는 Framework 
· #import <UIKit/UIKit.h> 로 추가함

UI 클래스 계층도 

· 오버라이드를 통한 기능 구현에서 알 수 있듯이, 부모관계와 상속 가능 여부를 알아야 함

UI Responder 

UI View 
· 가장 기본이 되는 뷰
· UIComponent들의 조합으로 화면이 구성되며, UIview를 상속받음…즉 iOS화면구성은 UIview의 집합으로 되어 있음

UIView Class
· 외워야 하는 주요한 항목들임
프레임 : x 좌표 y 좌표 width height 값이 들어가는 구조체… “0,0,0,0”
바운즈 : 무조건 0,0,width,height 
센터 : UI의 중심 …x, y 좌표값은 메인 뷰 기준임…
UI컬러 : 배경색…디폴트는 흰색
알파 : 뷰의 투명도값
히든 : 숨김, 아예 안보이게 하기, 액션 조차 받지 않음…(투명도는 설정해도 액션은 받음)
컨텐츠모드
틴트컬러 · iOS7부터 등장…기본 베이스컬러 설정…”자기 하위 뷰에 모두 영향을 줌”

“파라미터로 받는 뷰를 나 자신의 하이 뷰로 설정하겠다”
리무브 프롬 슈퍼뷰 : “내 위의 상위 뷰 부터 지워달라”

UIview 예제

  UIView *myView = [[UIView alloc] initWithFrame:CGRectMake(0, 0, 100, 300)];
    
    //객체생성
    
    myView.backgroundColor = [UIColor blueColor];
    //배경색 변경
    
    [self.view addSubview:myView];
    
    UIView *subView = [[UIView alloc] initWithFrame:CGRectMake(10, 30, 100, 200)];
    subView.frame = CGRectMake(10, 30, 50, 200);
    [subView setBackgroundColor:[UIColor redColor]];
    [myView addSubview:subView];

