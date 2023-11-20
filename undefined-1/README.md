# 초기 설정

AWS MGN을 사용하여 서버를 마이그레이션하기 전에 다음 단계에 따라 초기 설정을 완료해야 합니다.

* 대상 AWS 계정 및 리전(이 워크샵에서는 **US West (Oregon)** (`us-west-2`) 리전)에서 AWS MGN 서비스를 시작합니다.&#x20;
* AWS Replication agents(소스 서버에 배포될 MGN 에이전트)가 AWS MGN 서비스로 인증할 때 사용할 IAM User를 생성합니다.&#x20;
* 대상 서버에 대한 **default launch template**을 생성합니다. 여기에는 새로 추가된 모든 소스 서버에 적용될 공통 파라미터 등이 포함됩니다(대상 서브넷, 보안 그룹, 인스턴스 유형 및 EBS 볼륨 유형).
* 대상 서버가 **AWS Systems Manager**와 자동으로 통합되어 다양한 SSM 초기화 후 작업을 사용할 수 있도록 하는 **default post-launch actions**을 구성합니다.
