# 환경 살펴보기

현재 온프레미스에서 실행되는 프로덕션 환경은 단일 애플리케이션의 일부로 2개의 서버가 구성되어 있습니다.

| Application | Hostname      | FQDN	                       | OS      | Platform   |
| ----------- | ------------- | --------------------------- | ------- | ---------- |
| WordPress   | wordpress-web | wordpress-web.onpremsim.env | Centos7 | Apache+PHP |
| WordPress   | wordpress-db  | wordpress-db.onpremsim.env  | Centos7 | MariaDB    |

{% hint style="info" %}
이 가이드에서 제시된 모든 명령은 바스티온 호스트 내부에서 실행해야 합니다.
{% endhint %}

1. 마이그레이션할 애플리케이션을 테스트합니다. 배스천 호스트에서 Chrome 브라우저를 사용하여 다음 URL을 엽니다.

{% hint style="info" %}
이 실습에서는 Chrome 브라우저를 사용할 것을 권장합니다. Internet Explorer 브라우저를 사용하려면 추가 구성이 필요하므로 실습에 시간이 더 소요될 수 있습니다.
{% endhint %}

| Application | URL                                                                        |
| ----------- | -------------------------------------------------------------------------- |
| Wordpress   | [http://wordpress-web.onpremsim.env/](http://wordpress-web.onpremsim.env/) |

다음 필드에서 해당 URL을 복사할 수 있습니다.

```
http://wordpress-web.onpremsim.env/
```

2. 워드프레스 사이트가 로딩 됩니다.

간단한 테스트이므로 애플리케이션 웹페이지가 표시되는지 확인하기만 하면 됩니다.
