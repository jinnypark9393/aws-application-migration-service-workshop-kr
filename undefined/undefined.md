# 배스천 호스트에 연결

이제 AWS 계정에 액세스할 수 있게 되었으니 다음 단계에 따라 배스천 호스트에 연결합니다.

1.  이 워크샵의 왼쪽 창에서 **AWS account access** 섹션을 찾은 다음 **Get EC2 SSH Key**를 선택합니다. 키를 복사하여 다음 단계에서 사용하여 Bastion 호스트에 연결해야 합니다.


2. 키를 복사하려면 오른쪽에 있는 작은 복사 아이콘을 선택합니다.



{% hint style="info" %}


이 키를 사용하여 Bastion 호스트에 RDP로 접속 합니다. 접속에는 두 가지 방법이 있습니다.

1. 컴퓨터에 로컬로 Windows 원격 데스크톱(RDP) 클라이언트가 설치되어 있는 경우, **옵션 (1) - RDP 로컬 클라이언트를 사용하여 연결**을 사용할 수 있습니다. 로컬 컴퓨터에 RDP 클라이언트가 설치되어 있지 않은 경우 워크샵을 시작하기 전에 데스크톱에 설치를 진행합니다.
2. 워크샵에서 바로 사용할 수 있는 RDP 클라이언트가 설치되어 있지 않은 경우, **옵션 (2) - Fleet Manager 원격 데스크톱을 사용하여 연결**을 사용할 수 있습니다. 이 경우 AWS 콘솔에 대한 HTTPS 액세스만 필요합니다.
{% endhint %}



{% tabs %}
{% tab title="옵션 (1) - RDP 로컬 클라이언트를 사용하여 연결" %}
1.  **AWS 콘솔** 검색 창에 EC2를 입력하고 **EC2 대시보드**로 이동합니다. 리소스에서 **인스턴스(실행 중)**를 선택합니다. 이 워크샵에 사용하는 인스턴스가 표시됩니다. 혹은  [AWS EC2 Console (Bastion host) ](https://us-west-2.console.aws.amazon.com/ec2/home?region=us-west-2#Instances:tag:Name=MID-Bastion)에 접속해 신규 브라우저 탭에서 AWS EC2 콘솔에서 `MID-Bastion` 인스턴스를 확인할 수도 있습니다.

    `MID-Bastion`이라는 인스턴스를 선택한 다음 화면 상단에서 **Connect**를 선택합니다.
2. 다음 화면에서 **RDP client** 탭을 선택합니다. **Connection Type** 에서 **Connect using RDP client** 옵션을 선택합니다. 배스천 호스트에 연결하려면 Administrator 계정의 비밀번호를 복호화해야 합니다. **Get password**를 선택합니다.
3. **Get Windows password** 화면에서 2번에서 불러온 키 페어를 선택해야 합니다. 키 페어를 복사한 경우에는 스크린샷과 같이 빈 상자에 붙여넣은 다음 **Decrypt password**를 선택하면 됩니다.
4. 원격 데스크톱 파일을 다운로드하고 비밀번호와 Administrator 사용자 이름을 사용하여 배스천 호스트에 연결합니다.
{% endtab %}

{% tab title="옵션 (2) - Fleet Manager 원격 데스크톱을 사용하여 연결" %}
1.  **AWS 콘솔** 검색 창에 EC2를 입력하고 **EC2 대시보드**로 이동합니다. 리소스에서 **인스턴스(실행 중)**를 선택합니다. 이 워크샵에 사용하는 인스턴스가 표시됩니다. 혹은  [AWS EC2 Console (Bastion host) ](https://us-west-2.console.aws.amazon.com/ec2/home?region=us-west-2#Instances:tag:Name=MID-Bastion)에 접속해 신규 브라우저 탭에서 AWS EC2 콘솔에서 `MID-Bastion` 인스턴스를 확인할 수도 있습니다.

    `MID-Bastion`이라는 인스턴스를 선택한 다음 화면 상단에서 **Connect**를 선택합니다.
2. 다음 화면에서 **RDP client** 탭을 선택합니다. **Connection Type**에서 **Connect using Fleet Manager** 옵션을 선택한 다음 **Fleet Manager Remote Desktop**을 선택합니다.
3. **Fleet Manager – Remote Desktop** 화면에서 **Key pair**를 선택합니다. **key pair content** 아래에서 **Paste key pair content**를 선택한 다음 2번에서 복사한 키 페어를 붙여넣습니다. **Connect**을 선택합니다.
4. Fleet Manager가 배스천 호스트에 원격 데스크톱 세션을 설정합니다. **Full Screen**을 선택하면 전체 화면으로 만들 수 있습니다.
{% endtab %}
{% endtabs %}

배스천 호스트에 연결했다면 Next를 클릭하여 다음 단계를 진행합니다.
