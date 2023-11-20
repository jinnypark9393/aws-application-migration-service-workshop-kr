# AWS Replication Agent 설치

**AWS Application Migration Service**는 소스 서버에 설치해야 하는 에이전트를 사용하여 데이터를 AWS로 복제합니다.

1. [여기](https://catalog.us-east-1.prod.workshops.aws/event/dashboard/en-US/workshop/rehost/gettingstarted/connect-to-bastion)에 설명된 대로 배스천 호스트 머신을 연결합니다.
2. Windows **배스천** 호스트 머신에서 **Putty**를 엽니다.
3. 애플리케이션당 각 서버에 대해 4개의 세션이 미리 구성되어 있습니다(각각 `-web` 및 `-db` 서버가 있는 `Offbiz`, `Wordpress`).
4. 네 대의 컴퓨터 모두에 **SSH**로 접속하고 메시지가 표시되면 사용자 **user** 및 **비밀번호**를 입력합니다.

```
AWSmgn23
```

{% hint style="info" %}
**참고**: PuTTY 세션에서 이미 '**user**'로 로그인하도록 구성되어 있으므로 사용자 이름 '**user**'를 별도로 입력하지 않아도 됩니다.
{% endhint %}

5. 설치 명령을 작성하고 에이전트를 실행하는 방법으로는 두 가지 옵션이 있습니다.

* AWS MGN 콘솔에서 **Source Servers** -> **Add server**(권장 방법) 사용
* 인스톨러를 위한 명령줄을 수동으로 생성 - 우측 탭 선택 사항의 설명을 사용

원하는 옵션을 선택하거나 다른 소스 서버에 대해 다른 옵션들을 활용합니다.

{% tabs %}
{% tab title="[기본]AWS MGN 콘솔에서 Replication Agent 설치" %}
1.
{% endtab %}

{% tab title="[선택 사항]AWS Replication Agent 설치 명령어를 수동으로 작성" %}

{% endtab %}
{% endtabs %}

6.
