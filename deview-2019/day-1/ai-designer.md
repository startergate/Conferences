# AI Designer : 스스로 디자인하는 AI [#](https://deview.kr/data/deview/2019/presentation/[146]%20AI%20Designer%20스스로%20디자인하는%20AI.pdf)

* Image Generation
* Image Translation
* Image Transfer

## Trend of I2I
=> 오직 1개의 Generator
* uni-modal
  * CycleGAN
  * UGATIT
* multi-domain
  * StarGAN
* multi-modal
  * MUNIT
  * DRIT
* multi-domain + modal ★
  * SDIT
  * DMIT
  
=> 아키텍처는 대표적으로 2개


## 논문은 왜 바로 안될까?
* 갯수와 퀄리티가 논문과 다름
  * 이미지 퀄리티를 높일 필요
    * Waifu2x 사용
* 특정 데이터셋에만 특화된 구조
  * Generator가 아닌 Discriminator를 수정해야
* target domain 변화 미비
  * => weight of adversarial_loss 증가
*  색감 유지 & shape 유지
  * => weight of reconstruction loss 증가
* Model Collapse
  * => weight of cyclic loss 증가
  
그래서...
* Real
  * 1:N
* Various Real (텍스쳐 합성)
  * 1:1
* Game Style (게임 스타일 합성)

