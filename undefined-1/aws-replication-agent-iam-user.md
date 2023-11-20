# AWS Replication Agent IAM User 생성

소스 서버에 설치될 AWS Replication Agent(MGN agent)는 소스 머신을 AWS MGN에 등록하기 위해 IAM 권한이 필요합니다. 이 단계에서는 다음 단계의 AWS Replication Agent에서 사용할 필수 IAM user를 생성합니다.

## IAM 콘솔을 통해 AWS Replication Agent IAM User 생성

1. **Find Services**에서 **IAM**을 검색하여 선택하거나 다음 링크를 사용하여 [IAM 콘솔](https://us-east-1.console.aws.amazon.com/iamv2/home?region=us-west-2#/home)을 엽니다.
2. **IAM** 기본 페이지의 왼쪽 탐색 메뉴에서 **Users**를 선택한 다음 **Add user**를 선택합니다.
3. **User name**에 `MGNuser`를 입력한 후 **Next**를 클릭합니다.
4. **Set Permissions** 페이지에서 다음을 수행합니다.

* **Permissions options** 섹션 우측에 있는 **Attach policies directly** 옵션을 선택합니다.
* **Permissions policies** 섹션의 필터 상자에 정책 이름 `AWSApplicationMigrationAgentInstallationPolicy`를 붙여넣고 _Enter_ 키를 눌러 필터를 추가합니다.

```
AWSApplicationMigrationAgentInstallationPolicy
```

* 해당 섹션의 정책 목록에서 찾은 정책을 선택했는지 확인합니다.

{% hint style="info" %}
다음 페이지로 이동하기 전에 `AWSApplicationMigrationAgentInstallationPolicy` 정책을 선택했는지 확인합니다.
{% endhint %}

* 마지막으로 **Next** 옵션을 선택합니다.

5. 내용을 확인합니다. 사용자 이름이 `MGNuser`이고 적절한 정책 `AWSApplicationMigrationAgentInstallationPolicy`가 사용자에 연결되어 있는지 확인합니다. 이 워크샵에서는 IAM user에 태그를 추가하지 않습니다. **Create user**를 선택합니다.

{% hint style="info" %}
다음 페이지로 이동하기 전에 Permissions Summary 섹션의 AWSApplicationMigrationAgentInstallationPolicy가 사용자에게 추가되었는지 확인합니다. 그렇게 하지 않으면 에이전트가 작동할 수 있는 충분한 권한이 없기 때문에 AWS Replication Agent 설치 단계 중에 워크샵에서 권한 오류가 추가로 발생할 수 있습니다.
{% endhint %}

6. **User created successfully**라는 녹색 배너에서 **View user**를 선택하여 프로그래밍 방식 액세스를 추가합니다.
7. **Security credentials**을 선택합니다.
8. **Access keys** 섹션까지 이동하여 **Create access key**를 선택합니다.
9. **Application running outside AWS**를 선택한 후 **Next**를 선택합니다.
10. 이 워크샵의 경우 태그를 추가하지 않고 **Create access key**를 선택하세요.
11. 다음 페이지에 액세스 키가 성공적으로 생성되었다는 확인 메시지가 표시되며, **AWS Replication Agent**를 설치하는 데 필요한 **Access key ID**와 **Secret access key**를 복사할 수 있습니다. 먼저 **Download .csv** 옵션을 선택하고 자격 증명이 포함된 파일을 저장했는지 확인한 다음 "Done"을 선택합니다.

소스 서버에 AWS Replication Agent를 설치하려면 **Access key ID**와 **Secret access key**가 필요합니다. 이 정보는 **Download .csv** 옵션을 선택하여 .csv 파일로 저장할 수 있습니다.

{% hint style="info" %}
다음 단계를 진행하기 전에 반드시 **Download .csv** 버튼을 선택하고 데스크톱에서 CSV 파일을 열어야 합니다.

해당 페이지를 닫으면 방금 생성한 IAM user의 자격 증명을 다운로드할 수 있는 방법이 없습니다.
{% endhint %}

***

IAM user를 성공적으로 만들고 **자격 증명이 포함된 CSV 파일을 다운로드**했다면 다음 단계를 진행합니다.

***
