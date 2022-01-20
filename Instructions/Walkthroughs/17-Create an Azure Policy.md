---
wts:
    title: '17 - Azure Policy 만들기(10분)'
    module: '모듈 05: ID, 거버넌스, 개인 정보 및 규정 준수 기능에 대해 설명하기'
---
# 17 - Azure Policy 만들기(10분)

이 연습에서는 Azure 리소스의 배포를 특정 위치로 제한하는 Azure Policy를 만듭니다.

# 작업 1: 정책 할당 만들기 

이 작업에서는 허용된 위치 정책을 구성하고 구독에 할당합니다. 

1. [Azure Portal](https://portal.azure.com)에 로그인합니다.

2. **모든 서비스** 블레이드에서 **정책**을 검색하여 선택하고 **작성** 섹션 아래에서 **정의**를 클릭합니다.  잠시 시간을 내서 기본 제공 정책 정의 목록을 검토합니다. 예를 들어 **범주** 드롭다운에서 **컴퓨팅**만 선택합니다. **허용되는 가상 머신 크기 SKU** 정의를 사용하면 조직에서 배포할 수 있는 일련의 가상 머신 SKU를 지정할 수 있습니다.

3. **정책** 페이지로 돌아가서 **작성** 섹션에서 **할당**을 클릭합니다. 할당은 특정 범위 내에서 수행하도록 할당된 정책입니다. 예를 들어 구독 범위에 정의를 할당할 수 있습니다. 

4. **정책 - 할당** 페이지의 위쪽에서 **정책 할당**을 클릭합니다.

5. **정책 할당** 페이지에서 기본 범위를 유지합니다.

      | 설정 | 값 | 
    | --- | --- |
    | 범위| **선택한 기본값 사용**|
    | 정책 정의 | 줄임표를 클릭한 다음 **허용된 위치**를 검색하고 |
    | 할당 이름 **선택** | **허용된 위치** |
    
    ![필드 값이 입력되고 선택 단추가 강조 표시된 범위 창의 스크린샷. ](../images/1402.png)
6. **매개 변수** 탭에서 **일본 서부**를 선택합니다. **검토 + 만들기**를 클릭하고 **만들기**를 클릭합니다.

    **참고**: 범위는 정책 할당이 적용되는 리소스 또는 리소스 그룹을 결정합니다. 이 경우에는 이 정책을 특정 리소스 그룹에 할당할 수 있지만 구독 수준에서 정책을 할당하기로 결정했습니다. 범위 구성에 따라 리소스가 제외될 수 있다는 점에 유의하세요. 제외는 선택 사항입니다.

    **참고**: 이 **허용된 위치** 정책 정의는 모든 리소스를 배포해야 하는 위치를 지정합니다. 다른 위치를 선택하면 배포가 허용되지 않습니다. 자세한 내용은 [Azure Policy 샘플](https://docs.microsoft.com/ko-kr/azure/governance/policy/samples/index) 페이지를 참조하십시오.

   ![사용 가능한 정의 창의 스크린샷. 다양한 필드가 강조 표시되어 있고 관리 디스크를 사용하지 않는 VM 감사 옵션이 선택되어 있습니다.](../images/1403.png)

9. 이제 **허용된 위치** 정책 할당이 **정책 - 할당** 창에 표시되며, 지정한 범위 수준(구독 수준)에서 정책을 적용합니다.

# 작업 2: 허용된 위치 정책 테스트

이 작업에서는 허용된 위치 정책을 테스트합니다. 

1. Azure Portal의 **모든 서비스** 블레이드에서 **스토리지 계정**을 검색하여 선택한 다음 **+만들기**를 선택합니다.

2. 스토리지 계정을 구성합니다(스토리지 계정 이름에서 **xxxx**를 문자와 숫자로 대체하여 이름을 전역적으로 고유하게 지정). 다른 항목은 기본값을 사용합니다. 

    | 설정 | 값 | 
    | --- | --- |
    | 구독 | **제공된 기본값 사용** |
    | 리소스 그룹 | **myRGPolicy**(새로 만들기) |
    | 스토리지 계정 이름 | **storageaccountxxxx** |
    | 위치 | **(미국) 미국 동부** |

3. **검토 + 만들기**를 클릭한 다음, **만들기**를 클릭합니다. 

4. **허용된 위치** 정책 이름을 포함하여 정책에서 해당 리소스를 허용하지 않는다는 내용의 **배포 실패** 오류가 표시됩니다.

# 작업 3: 정책 할당 삭제

이 작업에서는 허용된 위치 정책 할당을 제거하고 테스트합니다. 

향후 수행하려는 작업이 차단되지 않도록 정책 할당을 삭제합니다.

1. **모든 서비스** 블레이드에서 **정책**을 검색하여 선택한 다음 **허용된 위치** 정책을 클릭합니다.

    **참고**: **정책** 블레이드에서 할당한 다양한 정책의 규정 준수 상태를 볼 수 있습니다.

    **참고**: 허용된 위치 정책에 비준수 리소스가 표시될 수 있습니다. 이 경우 이러한 리소스는 정책 할당 전에 만들어진 리소스입니다.
 
2. **허용된 위치**를 클릭하면 허용된 위치 정책 규정 준수 창이 열립니다.

3. 최상위 메뉴에서 **할당 삭제**를 클릭합니다. **예**를 클릭하여 정책 할당 삭제를 확인합니다.

   ![할당 삭제 메뉴 항목의 스크린샷.](../images/1407.png)

4. 다른 스토리지 계정을 만들어 정책이 더 이상 적용되지 않는지 확인합니다.

    **참고**: **허용된 위치** 정책이 유용할 수 있는 일반적인 시나리오는 다음과 같습니다. 
    - *비용 추적*: 다른 지역 위치에 대해 다른 구독이 있을 수 있습니다. 정책은 비용 추적에 도움이 될 수 있게 모든 리소스가 의도한 지역에서 배포되도록 합니다. 
    - *데이터 보존 및 보안 규정 준수*: 또한 데이터 보존 요구 사항이 있는 경우 고객 또는 특정 워크로드별로 구독을 만들고 모든 리소스를 특정 데이터 센터에 배포하도록 정의하면 데이터 및 보안 규정 준수 요구 사항을 준수할 수 있습니다.

축하합니다. Azure 리소스의 배포를 특정 데이터 센터로 제한하는 Azure Policy를 만들었습니다.

**참고**: 이 리소스 그룹을 제거해 추가 비용이 발생하는 것을 방지할 수도 있습니다. 리소스 그룹을 검색하고 리소스 그룹을 클릭한 다음 **리소스 그룹 삭제**를 클릭합니다. 리소스 그룹의 이름을 확인한 다음 **삭제**를 클릭합니다. **알림**을 모니터링하여 삭제가 어떻게 진행되는지 확인합니다.