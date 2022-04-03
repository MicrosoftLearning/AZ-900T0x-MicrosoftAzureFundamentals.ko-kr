---
wts:
  title: 02 - 웹앱 만들기(10분)
  module: Module 02 - Core Azure Services (Workloads)
ms.openlocfilehash: 7b7acc368eff3c653579d54a12828e02a615a672
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/27/2022
ms.locfileid: "137908633"
---
# <a name="02---create-a-web-app-10-min"></a>02 - 웹앱 만들기(10분)

이 연습에서는 Docker 컨테이너를 실행하는 웹앱을 만듭니다. Docker 컨테이너는 시작 메시지를 포함합니다. 

Azure App Service는 웹 애플리케이션의 호스팅 및 실행을 지원하도록 설계된 4가지 서비스의 모음입니다. 4가지 서비스(Web Apps, Mobile Apps, API Apps 및 Logic Apps)는 모습은 다르지만 모두 매우 유사한 방식으로 작동합니다. Web Apps는 4가지 서비스 중 가장 일반적으로 사용되는 서비스이며 이 랩에서 사용할 서비스입니다.

# <a name="task-1-create-a-web-app"></a>작업 1: 웹앱 만들기 

이 작업에서는 Azure App Service 웹앱을 만듭니다. 

1. [Azure 포털](http://portal.azure.com/)에 로그인합니다. 

2. **모든 서비스** 블레이드에서 **App Services** 를 검색하여 선택하고 **+ 추가, + 만들기, + 새로 만들기** 를 클릭합니다.

3. **웹앱** 블레이드의 **기본** 탭에서 다음 설정을 지정합니다(웹앱 이름의 **xxxx** 를 문자와 숫자로 대체하여 전역적으로 고유한 이름 지정). App Service 계획을 포함한 다른 모든 기본값을 그대로 둡니다. 

    | 설정 | 값 |
    | -- | -- |
    | 구독 | **제공된 기본값 사용** |
    | 리소스 그룹 | **새 리소스 그룹 만들기**|
    | Name | **myDockerWebAppxxxx** |
    | 게시 | **Docker 컨테이너** |
    | 운영 체제 | **Linux** |
    | 지역 | **미국 동부** |
    
    **참고:** **xxxx** 를 고유한 웹앱 이름으로 변경하는 것을 잊지 마세요.

4. **다음 > Docker** 를 클릭하고 컨테이너 정보를 구성합니다.  

    | 설정 | 값 |
    | -- | -- |
    | 옵션 | **단일 컨테이너** |
    | 이미지 원본 | **Docker Hub** |
    | 액세스 형식 | **공용** |
    | 이미지 및 태그 | **mcr.microsoft.com/azuredocs/aci-helloworld** |
    
 **참고:** 시작 명령은 선택 사항이며 이 연습에서는 필요하지 않습니다.

5. **검토 + 만들기** 를 클릭한 다음 **만들기** 를 클릭합니다. 

# <a name="task-2-test-the-web-app"></a>작업 2: 웹앱 테스트

이 작업에서는 웹앱을 테스트합니다.

1. 웹앱이 배포될 때까지 기다립니다.

2. **알림** 에서 **리소스로 이동** 을 클릭합니다. 

3. **개요** 블레이드에서 **URL** 을 찾습니다. URL을 클립보드에 복사합니다.

    ![웹앱 속성 블레이드의 스크린샷. URL이 강조 표시되어 있음.](../images/0801.png)

4. 새 브라우저 창에서 URL을 붙여넣은 다음, Enter 키를 누릅니다. Azure Container Instances에 오신 것을 환영합니다! 환영 메시지가 표시됩니다.

    ![Azure Container Instance 시작 페이지의 스크린샷.](../images/0802.png)

5. 웹앱의 **개요** 블레이드로 다시 전환하고 아래로 스크롤합니다. 데이터 입력/출력 및 요청을 추적하는 여러 개의 차트가 표시됩니다. 4단계를 몇 번 반복하면 차트에 해당 원격 분석 결과가 표시되는 것을 볼 수 있습니다. 여기에는 요청 수와 평균 응답 시간이 포함됩니다. 

**참고**: 이 리소스 그룹을 제거해 추가 비용이 발생하는 것을 방지할 수도 있습니다. 리소스 그룹을 검색하고 리소스 그룹을 클릭한 다음 **리소스 그룹 삭제** 를 클릭합니다. 리소스 그룹의 이름을 확인한 다음 **삭제** 를 클릭합니다. **알림** 을 모니터링하여 삭제가 어떻게 진행되는지 확인합니다.

축하합니다. Azure App Service를 만들었습니다.
