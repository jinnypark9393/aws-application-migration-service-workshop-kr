# AWS MGN 서비스 구성

Application Migration Service는 복제를 수행해야 하는 각 AWS 계정 및 리전에서 처음 사용할 때 초기화해야 합니다. 첫 번째 단계는 복제 설정 템플릿을 생성한 다음, 서비스가 작동하는 데 필요한 IAM 역할을 생성하여 서비스를 초기화하는 것입니다.

{% hint style="info" %}
Application Migration Service는 AWS 계정의 관리자 사용자만 초기화할 수 있습니다.
{% endhint %}



<details>

<summary>AWS MGN 초기화 중에 생성되는 IAM 역할</summary>

* AWSServiceRoleForApplicationMigrationService
* AWSApplicationMigrationReplicationServerRole
* AWSApplicationMigrationConversionServerRole
* AWSApplicationMigrationMGHRole
* AWSApplicationMigrationLaunchInstanceWithSsmRole
* AWSApplicationMigrationLaunchInstanceWithDrsRole
* AWSApplicationMigrationAgentRole

Application Migration Service 역할 및 관리 정책에 대한 자세한 내용은 [여기](https://docs.aws.amazon.com/mgn/latest/ug/mgn-initialize-console.html)에서 확인할 수 있습니다.

</details>

복제 설정은 소스 서버에서 AWS로 데이터를 복제하는 방법을 결정합니다. 복제 설정 템플릿으로 소스 서버를 Application Migration Service에 추가하기 전에 구성해야 할 복제 설정을 관리할 수 있습니다.

추후에 복제 설정 템플릿을 **편집**할 수 있습니다. 편집 후 복제 설정 템플릿에서 구성된 설정이 새로 추가된 각 서버로 전송됩니다. 서버를 Application Migration Service에 추가한 후에 각 서버의 복제 설정을 편집할 수도 있습니다.

1. [AWS Application Migration Service console](https://us-west-2.console.aws.amazon.com/mgn/home?region=us-west-2)에서 **Get started**를 선택합니다.
2. AWS Application Migration Service에 처음 접속할 때 서비스를 초기화하라는 메시지가 자동으로 표시됩니다. **Set up service**을 선택합니다.
3. Application Migration Service가 초기화되면 Application Migration Service 콘솔의 **Source Servers** 페이지로 리디렉션됩니다. 왼쪽 탐색 메뉴의 **Settings**에서 **Replication template**을 선택한 다음 **Edit template**을 선택합니다.
4. **Edit replication template** 화면에서 다음 값을 입력합니다.

* **Replication server configuration** 섹션
  * **Staging area subnet** 하위의 **StagingPublic** 서브넷을 선택합니다.
  * Replication Server instance type의 기본값을 그대로 유지합니다(t3.small 또는 t2.small 또는 다른 유형).

{% hint style="info" %}
아래 스크린샷과 동일하게 StagingPublic 서브넷을 선택해야 합니다. 이 옵션을 선택하지 않으면 나중에 워크샵에서 네트워크 통신 오류가 발생할 수 있습니다.
{% endhint %}





{% hint style="info" %}
마지막 섹션인 **Replication resources tags**까지 추가로 설정을 변경할 필요가 없이 다른 모든 값을 기본값으로 할당된 상태로 유지합니다.
{% endhint %}

* 볼륨 섹션의 기본값을 그대로 유지합니다
  * EBS 볼륨 유형(500GiB 이상의 디스크 복제용)을 gp3로 설정(기본값 그대로 유지)
  * EBS 암호화 - 기본값(기본값 그대로 유지)
* **Security groups** 섹션에서 기본값을 유지합니다.
  * **Always use Application Migration Service security group**란이 선택되어 있음(기본값 그대로 유지)
  * **Additional security groups** Dropbox 비우기 - 추가 보안 그룹을 선택하지 않음(기본값 그대로 유지)
* **Data routing and throttling** 섹션의 기본값을 그대로 유지합니다.
  * 첫 번째 옵션인 **Create public IP** 선택
  * 다른 옵션은 선택하지 않음

{% hint style="info" %}
아래 스크린샷과 동일하게 첫 번째 옵션인 **Create public IP**을 선택했는지 확인합니다. 이 옵션을 선택하지 않으면 나중에 워크샵에서 네트워크 통신 오류가 발생할 수 있습니다.
{% endhint %}

* \[선택 사항] 마지막 섹션인 **Replication resources tags**에서 **Add new tag** 버튼을 눌러 스테이징 영역에서 생성된 모든 리소스에 적용할 태그를 구성합니다.
  * Key 태그 추가: `Environment`(아래 섹션에서 복사하여 붙여넣기)
  * Value 태그 추가: `Migration-Staging`

```
Environment
```

```
Migration-Staging
```

{% hint style="info" %}
이를 통해 스테이징 영역에서 마이그레이션 프로세스 중 AWS MGN이 임시로 생성한 리소스의 **비용을 제어**할 수 있습니다.
{% endhint %}

* **Save template**을 선택하여 복제 설정 템플릿 구성을 완료합니다.

4. AWS MGN 콘솔에 복제 설정 템플릿이 저장되었음을 확인하는 녹색 배너가 표시됩니다.
