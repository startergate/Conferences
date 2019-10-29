# console.warn('좀 불안하지?') //node.js 모니터링을 위한 pinpoint node agent 개발기 [#](https://deview.kr/data/deview/2019/presentation/[226]+console.warn.pdf)
JS 모니터링 툴의 부재
=> 가시성!

APM?
* Application Performance Management
* New Relic
  * 비쌈
* Elastic
  * 사후 처리의 느낌이 강함
* Skyapm

PINPOINT!

Monkey Patching
* Code Coverage in V8?
  * 이렇게 하려면 V8 엔진 자체를 뜯어야 했음
* 코드를 뜯는데요

비동기 추적
* async_hooks

Apply Modules

`require('pinpoint-node-agent')`