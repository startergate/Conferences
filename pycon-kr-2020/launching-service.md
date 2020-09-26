# [글로벌 방송국 서비스 1인 개국기](https://pycon.kr/2020/program/talk/14)
* FastAPI?
 * pydantic orm_mode로 django 모델 다룸

* Django Admin Customization만으로 비즈니스 로직 & UI 대부분 해결 가능

* 서비스 변경 가능성을 예측하여 모델 설계
 * blank=True, default='', null=True가 지속 변경 가능 스펙 대응 용이
 * 외부 키는 SET_NULL로
 
* 절대 안 변할 열거형만 Field.choices

* 캐싱을 사용하는 경우 헤더 인증에서는 풀리는 경우가 있음 => 그래서 쿠키를 사용
