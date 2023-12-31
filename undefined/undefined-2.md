# 진행 팁

## 아래로 스크롤하여 자세한 설명을 확인

{% hint style="info" %}
해당 페이지의 모든 단계를 완료할 때까지 각 페이지 끝으로 스크롤합니다.
{% endhint %}

## 워크샵 설명서의 내용을 복사하여 붙여넣기

명령을 복사하라는 메시지가 표시되면 트레이 창에서 아이콘을 선택하여 클립보드에 복사합니다.

## 복사한 내용을 Bastion 호스트에 붙여넣기

이 실습에서는 AWS 콘솔에서 Microsoft 메모장 또는 Microsoft 명령 프롬프트에 콘텐츠를 복사하여 붙여넣는 단계를 실습해보겠습니다.

복사하여 붙여넣는 방법에는 여러 가지가 있습니다. 복사 및 붙여넣기에 문제가 있는 경우, 아래의 **PowerShell** 및 **PuTTy** 창에 대해 다음 방법들을 시도해 보세요.

### **PowerShell 창에서 작업하기**

1. Powershell 창에서 context 메뉴를 사용할 수 있습니다. 제목 표시줄을 마우스 오른쪽 버튼으로 클릭한 다음 **Edit** -> **Paste**를 선택합니다.
2. 키보드 단축키를 사용할 수 있습니다: Ctrl-C / Ctrl-V
3. PowerShell 창이 이미 선택되어 있는 경우 마우스 오른쪽 버튼을 직접 클릭할 수도 있습니다. 이 작업은 세 단계로 수행할 수 있습니다
   1. 버퍼에 명령을 복사
   2. PowerShell 창의 제목을 클릭하면 커서가 명령줄에 활성화됩니다(필요한 경우 입력을 시작할 수 있습니다).
   3. 마우스 오른쪽 버튼을 클릭하면 복사된 명령이 커서  위치에 붙여넣어집니다.

{% hint style="info" %}
참고: 제목(위 2번 단계)을 클릭하지 않고 대신 PowerShell 창 내부를 클릭하면 선택 모드가 활성화되고 선택된 영역이 클립보드에 복사되어 위 1단계에서 복사한 내용을 대체하는 **반대** 효과가 나타납니다.
{% endhint %}

### PuTTy 창에서 작업하기

1. PuTTy 창에서 마우스 오른쪽 클릭으로 붙여넣기를 할 수 있으며, 창 내부에서는 실수로 클릭해도 클립보드를 덮어쓰지 않으므로 우클릭으로 붙여넣기 전에 PuTTy 창의 제목을 클릭할 필요가 없습니다.&#x20;
2. PowerShell 창과 달리 PuTTy는 표준 키보드 단축키를 지원하지 않으며 context 메뉴가 없습니다. 마우스 우클릭을 사용하는 것이 PuTTy 창에 내용을 붙여넣는 가장 좋은 방법입니다.&#x20;

{% hint style="info" %}
비밀번호 붙여넣기는 보안상의 이유로 화면에 표시되지 않는다는 점에 유의합니다.
{% endhint %}
