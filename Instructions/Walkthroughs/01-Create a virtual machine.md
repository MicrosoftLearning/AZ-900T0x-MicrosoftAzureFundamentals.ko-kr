---
wts:
    title: '01 - 포털에서 가상 머신 만들기(10분)'
    module: '모듈 02 - 핵심 Azure 서비스(워크로드)'
---
# 01 - 포털에서 가상 머신 만들기(10분)

이 연습에서는 Azure Portal에서 가상 머신을 만들고 이 가상 머신에 연결하여 웹 서버 역할을 설치하고 테스트합니다. 

**참고**: 이 연습을 수행하는 동안 정보 아이콘을 클릭하고 읽으세요. 

# 작업 1: Azure 가상 머신 만들기 
1. **https://portal.azure.com** 에서 Azure Portal에 로그인합니다.

3. Portal 메뉴의 **모든 서비스** 블레이드에서 **가상 머신**을 검색하고 선택한 다음 **+추가, +만들기 및 +새로 만들기**를 클릭하고 드롭다운에서 **+가상 머신**을 선택합니다.

4. **기본** 탭에서 다음 정보를 채웁니다(다른 항목은 기본값을 사용).

    | 설정 | 값 |
    |  -- | -- |
    | 구독 | **제공된 기본값 사용** |
    | 리소스 그룹 | **새 리소스 그룹 만들기** |
    | 가상 머신 이름 | **myVM** |
    | 지역 | **(미국) 미국 동부**|
    | 가용성 옵션 | 인프라 중복 옵션 필요 없음|
    | 이미지 | **Windows Server 2019 Datacenter - Gen2**|
    | 크기 | **Standard D2s v3**|
    | 관리자 계정 사용자 이름 | **azureuser** |
    | 관리자 계정 암호(정확하게 입력!) | **Pa$$w0rd1234**|
    | 인바운드 포트 규칙 - | **선택한 포트 허용**|
    | 인바운드 포트 선택 | **RDP(3389)** 및 **HTTP(80)**| 

5. 네트워킹 탭으로 전환하여 **인바운드 포트 선택** 섹션에서 **HTTP(80) 및 RDP(3389)** 가 선택되어 있는지 확인합니다.

6. 관리 탭으로 전환하고 **모니터링** 섹션에서 다음 설정을 선택합니다.

    | 설정 | 값 |
    | -- | -- |
    | 부팅 진단 | **사용 안 함**|

7. 나머지 값은 기본값을 그대로 유지한 후 페이지 아래쪽에 있는 **검토 + 만들기** 단추를 클릭합니다.

8. 유효성 검사가 통과되면 **만들기** 단추를 클릭합니다. 가상 머신을 배포하는 데 약 5~7분이 걸릴 수 있습니다.

9. 배포 페이지 및 **알림** 영역(위쪽 메뉴 모음의 종 모양 아이콘)에서 업데이트를 받게 됩니다.

# 작업 2: 가상 머신에 연결

이 작업에서는 RDP(원격 데스크톱 프로토콜)를 사용하여 새 가상 머신에 연결합니다. 

1. 상단 파란색 도구 모음에서 종 아이콘을 클릭하고, 배포가 성공하면 '리소스로 이동'을 선택합니다. 

    **참고**: 배포 페이지에서 **리소스로 이동** 링크를 사용할 수도 있습니다. 

2. 가상 머신 **개요** 블레이드에서 **연결** 단추를 클릭하고 드롭다운에서 **RDP**를 선택합니다.

    ![연결 단추가 강조 표시된 가상 머신 속성의 스크린샷.](../images/0101.png)

    **참고**: 다음 지침은 Windows 컴퓨터에서 VM에 연결하는 방법을 알려줍니다. Mac에서는 Mac App Store의 원격 데스크톱 클라이언트와 같은 RDP 클라이언트가 필요하고, Linux 컴퓨터에서는 오픈 소스 RDP 클라이언트를 사용할 수 있습니다.

2. **가상 머신에 연결** 페이지에서 포트 3389를 통해 공용 IP 주소로 연결하는 기본 옵션을 유지하고 **RDP 파일 다운로드**를 클릭합니다. 화면 왼쪽 아래에서 파일이 다운로드됩니다.

3. **열기**를 클릭하여 다운로드한 RDP 파일(랩 컴퓨터의 왼쪽 아래에 있음)을 열고 메시지가 표시되면 **연결**을 클릭합니다. 

    ![연결 단추가 강조 표시된 가상 머신 속성의 스크린샷. ](../images/0102.png)

4. **Windows 보안** 창에서 VM **azureuser**를 만들 때 사용했던 관리자 자격 증명과 암호(**Pa$$w0rd1234**)를 사용하여 로그인합니다. 

5. 로그인 프로세스 중에 인증서 경고가 표시될 수 있습니다. **예**를 클릭하거나 연결을 만들고 배포된 VM에 연결합니다. 성공적으로 연결되어야 합니다.

    ![사용자에게 신뢰할 수 없는 인증서를 알리는 메시지와 예 단추가 강조 표시된 인증서 경고 대화 상자의 스크린샷. ](../images/0104.png)

랩 내에서 새 가상 머신(myVM)이 시작됩니다. 서버 관리자 창과 대시보드 창이 나타나면 닫습니다(오른쪽 위의 "x" 클릭). 가상 머신의 파란색 배경이 표시됩니다. **축하합니다!** Windows Server를 사용하여 가상 머신을 배포하고 연결했습니다. 

# 작업 3: 웹 서버 역할 설치 및 테스트

이 작업에서는 방금 만든 가상 머신의 서버에 웹 서버 역할을 설치하고 기본 IIS 시작 페이지가 표시되는지 확인합니다. 

1. 새로 연 가상 머신의 검색 창에서 **PowerShell**을 검색하여 PowerShell을 시작하고, 검색되면 **Windows PowerShell**을 마우스 오른쪽 단추로 클릭하여 **관리자 권한으로 실행**합니다.

    ![시작 단추가 클릭되어 있고 PowerShell이 선택되어 있으며 관리자로 실행이 강조 표시되어 있는 가상 머신 데스크톱의 스크린샷.](../images/0105.png)

2. PowerShell에서 다음 명령을 실행하여 가상 머신에 **Web-Server** 기능을 설치합니다. 명령에 붙여넣고 설치를 시작하려면 ENTER 키를 누릅니다.

    ```PowerShell
    Install-WindowsFeature -name Web-Server -IncludeManagementTools
    ```
  
3. 명령을 완료하면 **Success** 메시지와 **True** 값이 표시됩니다. 설치를 완료하기 위해 가상 머신을 다시 시작하지 않아도 됩니다. 가상 머신의 중앙 상단에 있는 파란색 막대에서 **x**를 클릭하여 VM에 대한 RDP 연결을 닫습니다. 중앙 상단의 파란색 막대에서 **-** 를 클릭하여 최소화할 수도 있습니다.

    ![Install-WindowsFeature -name Web-Server -IncludeManagementTools 명령이 성공적으로 완료되었고 이를 알려주는 출력이 표시된 Windows PowerShell 명령 프롬프트의 스크린샷.](../images/0106.png)

4. Portal로 돌아가서 myVM의 **개요** 블레이드로 돌아간 다음 **클립보드에 복사** 단추를 사용하여 myVM의 공용 IP 주소를 복사한 후 새 브라우저 탭을 엽니다. 복사한 공용 IP 주소를 URL 텍스트 상자에 붙여넣고 **Enter** 키를 눌러 해당 주소로 이동합니다.

    ![IP 주소가 복사된 Azure Portal 가상 머신 속성 창의 스크린샷.](../images/0107.png)

5. 기본 IIS 웹 서버 시작 페이지가 표시됩니다.

    ![웹 브라우저에서 공용 IP 주소를 통해 액세스되는 기본 IIS 웹 서버 시작 페이지의 스크린샷.](../images/0108.png)

**축하합니다!** 공용 IP 주소를 통해 액세스할 수 있는 웹 서버를 실행하는 새 VM을 만들었습니다. 호스트할 웹 애플리케이션이 있는 경우 애플리케이션 파일을 가상 머신에 배포하고 배포된 가상 머신에서 공용 액세스를 위해 호스트할 수 있습니다.


**참고**: 이 리소스 그룹을 제거해 추가 비용이 발생하는 것을 방지할 수도 있습니다. 리소스 그룹을 검색하고 리소스 그룹을 클릭한 다음 **리소스 그룹 삭제**를 클릭합니다. 리소스 그룹의 이름을 확인한 다음 **삭제**를 클릭합니다. **알림**을 모니터링하여 삭제가 어떻게 진행되는지 확인합니다.
