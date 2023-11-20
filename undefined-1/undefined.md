# 기본 타겟 템플릿 구성

AWS MGN에서는 [**Launch Templates**](https://docs.aws.amazon.com/mgn/latest/ug/launch-template.html)과 [**Post-Launch templates** ](https://docs.aws.amazon.com/mgn/latest/ug/post-launch-settings.html)모두에 대해 대상 인스턴스 구성을 위한 기본 템플릿을 설정할 수 있습니다. 이러한 템플릿은 소스 서버에 **AWS Replication Agent**가 설치된 후, AWS MGN의 소스 서버 목록에 추가되는 모든 새 서버에 적용됩니다.

{% hint style="info" %}
기본 템플릿에 정의된 설정은 새로 추가된 각 소스 서버의 개별 구성에 복사되며, 나중에 서버별로 개별적으로 변경할 수 있습니다. 기본 템플릿의 설정은 이미 존재하고 복제 중인 서버에는 적용되지 않으며, 이러한 기본 템플릿을 변경해도 서버별 기존 개별 구성에는 영향을 미치지 않습니다.
{% endhint %}

{% hint style="info" %}
아래 두 템플릿을 모두 구성해야 합니다.

1. 대상 인스턴스의 향후 구성을 정의하는 **"Launch template"**&#x20;
2. 인스턴스가 AWS에서 성공적으로 시작된 후 트리거되는 자동화 작업을 정의하는 **"Post-launch template"**
{% endhint %}

<details>

<summary>1.기본 대상 인스턴스 구성 정의 - 'Launch Template'</summary>

**AWS MGN**은 [EC2 Launch Template](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-launch-templates.html)을 사용하여 테스트 및 컷오버 마이그레이션 단계에서 시작할 **대상 EC2 인스턴스**의 구성을 정의합니다.

[AWS Application Migration Service](https://us-west-2.console.aws.amazon.com/mgn/home?region=us-west-2#/launchTemplate) 콘솔로 이동하여 왼쪽 탐색 창의 **Settings** 메뉴에서 **Launch template**을 선택한 다음 **Edit**을 선택합니다.

* 이 페이지에서는 **새로 추가된 모든 소스 서버**에 대해 EC2 시작 템플릿을 구성하는 데 사용되는 **기본값**을 구성합니다.

구성해야 할 가장 중요한 값은 다음과 같습니다.

* 기본 **대상 서브넷** 및 **보안 그룹** - 인스턴스가 시작될 대상 위치 및 기본 네트워크 보안 구성을 정의합니다.&#x20;
* 기본 대상 **인스턴스 유형**(아래 설명을 참고), 또는 **기본** [인스턴스 크기 조정 권장 사항](https://docs.aws.amazon.com/mgn/latest/ug/right-sizing.html)에 따라 자동으로 대상 인스턴스 유형을 결정하도록 AWS MGN을 사용합니다. 참고: 이 기능을 활성화하면 EC2 Launch Template에 정의된 인스턴스 유형에 대한 모든 변경 사항을 덮어쓰게 됩니다.
* 대상 테스트/컷오버 EC2 인스턴스에 사용할 **EBS 볼륨**의 기본 유형
* 기본 네트워크 **보안 그룹** 또는 대상 테스트/컷오버 EC2 인스턴스에 연결할 기본 네트워크 보안 그룹 목록 및 기본 ENI(Elastic Network Interface)&#x20;

<!---->

* **서버 태그 전송** 기능을 활성화하여 AWS MGN을 통해 구성된 모든 태그를 대상 테스트/전환 인스턴스로 전송합니다.

아래 설명에 따라 이러한 파라미터를 기본값으로 설정합니다.

1. 첫 번째 일반 시작 설정 섹션에서

* _Activate instance type right-sizing_를 **선택 취소**하여 EC2 Launch Template 수준에서 대상 인스턴스 유형을 제어합니다(이 체크박스를 비활성화해야 아래 섹션의 **Default instance type** 필드를 사용할 수 있게 됩니다).
* **Transfer server tags** 체크박스를 선택하여 AWS MGN에 구성된 서버별 태그를 대상 인스턴스로 자동 복사할 수 있도록 합니다.

2. 아래로 이동해 **Default EC2 Launch Template** 섹션에서 EC2 Launch Template 내 일부 파라미터의 기본값을 설정할 수 있습니다.

* **Default target subnet** 드롭다운 메뉴를 선택하고 **TargetPrivate**이라고 표시된 서브넷을 선택합니다.
* 다음으로 **Additional security groups** 옵션을 선택하고 **TargetSecurityGroup**이라는 라벨이 붙은 보안 그룹을 선택합니다.
* 참고: 워크샵에서 _테스트 단계_용 보안 그룹과 향후 최종 상태 구성을 위한 보안 그룹이 두 개 있습니다. 이 워크샵에서는 기본 설정인 **TargetSecurityGroup**에 대한 최종 구성을 사용합니다. 실제 마이그레이션 시나리오에서는 테스트 단계에서는 다른 보안 그룹을 사용하고 나중에 전환하기 전에 최종 미래 상태의 "대상" 보안 그룹으로 교체하는 것을 권장합니다.
* **Default instance type**으로 `t3.small`을 사용합니다.
* 참고: 이 필드가 비활성화되어 있는 경우 위 섹션에서 **Activate instance type right-sizing**이 **꺼져 있는지** 확인합니다.

<!---->

* EBS 볼륨의 나머지 값은 기본값으로 그대로 둡니다.
  * `EBS volume type`: **General Purpose SSD (gp3)** 볼륨 유형
  * `IOPS`: 3000
  * `Throughput`: 125

3. **MAP program tagging**을 기본값(설정되지 않음)으로 두고 **Save template**을 선택하여 기본 EC2 Launch Template 설정을 저장합니다.

</details>

<details>

<summary>2.대상 인스턴스에 대한 기본 시작 후 자동화 작업 정의 - 'Post-launch template'</summary>

**AWS MGN**은 **Post-Launch Template** 설정을 사용하여 테스트/컷오버 인스턴스를 성공적으로 실행한 **이후의** 대상 EC2 인스턴스에서 실행할 모든 시작 후 자동화 작업을 정의합니다. 이 단계에서는 마이그레이션된 서버와 [AWS Systems Manager](https://docs.aws.amazon.com/systems-manager/latest/userguide/what-is-systems-manager.html)와의 통합을 구성하기 위해 AWS MGN Post-Launch **default template**을 사용합니다. 이렇게 하면 플릿 관리, 인벤토리, 패치 관리, 원격 실행, 자동화 문서 실행과 같은 AWS Systems Manager 기능이 자동으로 활성화됩니다.

### 기본 Post-Launch template 구성

1. [AWS Application Migration Service](https://us-west-2.console.aws.amazon.com/mgn/home?region=us-west-2#/postLaunchTemplate) 콘솔로 이동하여 왼쪽 탐색 창의 **Settings** 메뉴에서 **Post-launch template**을 선택한 다음 **Edit**을 선택합니다.
2. `Install the Systems Manager agent and allow executing actions on launched servers`라는 토글을 선택합니다.
3. 테스트 및 컷오버 인스턴스 모두에 SSM Agent를 설치하도록 구성된 대로 **Deployment** 옵션을 유지합니다. **Save template** 버튼을 선택합니다.

*   참고:&#x20;

    SSM automation documents를 통해 트리거되는 추가 post-launch 작업을 활성화하려면 AWS Systems Manager 통합을 활성화해야합니다.

4. AWS System Manager Agent(SSM Agent) 통합을 사용하도록 Post-Launch template을 구성하고, 테스트 또는 컷오버 인스턴스가 성공적으로 시작되면 다른 SSM automation documents를 트리거할 수 있습니다.

이 워크샵에서는 추가 작업을 사용하지 **않습니다**. **Next**을 선택하여 소스 서버에 **AWS Replication Agent**를 배포하는 데 필요한 IAM 구성을 진행합니다.

</details>
