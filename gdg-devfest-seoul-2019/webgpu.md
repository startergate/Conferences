# WebGPU is coming
WebGPU - Next Generation Graphics API on the Web<br>
Like OpenGL -> Vulkan

왜 WebVulkan이 아닌가?
* Vulkan이 범용적이지 못함

## 배경 지식
* WebGL?

## WebGL의 문제점
* CPU에서의 속도가 느림
* 버전이 뒤떨어짐
* 최신 하드웨어와 맞지 않음

WebWorker를 쓸 수는 없나요?<br>
Offscreen Render를 하면 되지 않나요?

WebGL은 "compute" 기능 부재

## WebGPU는 어떻게 돌아갈까
* GPU 명령들의 재사용을 허라
  * JavaScript call이 줄어듬
* 멀티스레드
* "compute" 기능 추가

## Dawn 프로젝트

https://webgpu.io