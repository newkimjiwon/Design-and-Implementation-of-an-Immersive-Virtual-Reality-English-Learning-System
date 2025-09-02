# Design-and-Implementation-of-an-Immersive-Virtual-Reality-English-Learning-System

## 프로젝트 개요 (Overview)

이 프로젝트에서 저희는 대화형 AI 기술을 활용하여 **실감형 가상현실(VR) 영어 학습 시스템을 설계하고 구현**했습니다. [cite: 12, 49] [cite_start]코로나19 팬데믹 이후 비대면 교육의 중요성이 커진 상황에 주목했고 [cite: 9][cite_start], 시공간 제약 없이 몰입감 높은 학습 경험을 제공할 수 있는 VR 기술의 가능성을 보았습니다. [cite: 10, 36]

이를 위해 저희는 **편의점을 가상 학습 환경으로 구축**했습니다. [cite: 13] [cite_start]학습자는 이 환경 안에서 AI 기반 NPC(Non-Player Character)와 자유롭게 상호작용하며 실전과 같은 영어 대화를 연습할 수 있습니다. [cite: 13, 21] [cite_start]특히, 저희 시스템의 핵심은 AI 언어 모델을 통해 **학습자의 영어 문장에 대한 문법적, 상황적 피드백을 실시간으로 제공**하여 학습 효과를 극대화하는 것입니다. [cite: 14]

## 주요 기능 (Key Features)

저희가 구현한 시스템의 핵심 기능은 다음과 같습니다.

* [cite_start]**실감형 VR 학습 환경**: 높은 몰입감을 제공하기 위해 편의점 공간을 가상으로 구현했습니다. [cite: 13, 175]
* [cite_start]**AI NPC와의 상호작용**: AI 언어 모델인 ChatGPT 4.0을 NPC에 연동하여, 학습자가 자연스러운 영어 대화를 나눌 수 있도록 했습니다. [cite: 50, 124]
* [cite_start]**음성 기반 대화**: 실제 대화처럼 학습할 수 있도록 사용자의 음성을 STT(Speech-to-Text)로 변환하고, NPC의 응답은 TTS(Text-to-Speech)를 통해 음성으로 출력되게 구현했습니다. [cite: 47, 76, 95]
* [cite_start]**실시간 피드백**: 학습자가 말한 문장의 문법적 정확성과 상황적 적절성을 AI가 실시간으로 분석하여 피드백을 제공합니다. [cite: 14, 151, 177]
* [cite_start]**프롬프트 엔지니어링**: AI NPC가 편의점 직원이라는 역할을 일관되게 수행하고, 학습에 도움이 되는 답변을 생성하도록 프롬프트 엔지니어링 기법을 적용했습니다. [cite: 54, 128]

## 시스템 아키텍처 (System Architecture)

저희는 시스템을 **클라이언트-서버 구조**로 설계했습니다. 전체 데이터 처리 흐름은 다음과 같습니다.

<img width="1447" height="524" alt="시스템 구성과 흐름" src="https://github.com/user-attachments/assets/c8a34f07-26d9-412b-b20a-bc83d99ef064" />
*<p align="center">그림 1. 시스템의 구성과 흐름</p>*

1.  [cite_start]**클라이언트 (VR 환경)**: 사용자가 XR 기기를 착용하고 NPC에게 영어로 말을 걸면, 음성 데이터가 녹음됩니다. [cite: 75, 76] [cite_start]저희는 이 음성 데이터를 Google Cloud Speech-to-Text API를 이용해 텍스트로 변환했습니다. [cite: 76, 104]
2.  [cite_start]**서버**: 변환된 텍스트는 서버로 전송되어 DB에 저장됩니다. [cite: 77] [cite_start]저희는 **폴링(Polling) 방식**을 적용하여, 서버가 주기적으로 DB를 확인해 새로운 사용자 입력이 있는지 감지하도록 구현했습니다. [cite: 79] [cite_start]입력된 텍스트는 AI 언어 모델에 최적화된 프롬프트 스크립트로 변환되어 전달됩니다. [cite: 80]
3.  [cite_start]**응답 처리**: AI 모델이 생성한 답변 텍스트는 다시 DB에 업데이트된 후, 클라이언트로 전송됩니다. [cite: 81] [cite_start]클라이언트에서는 이 텍스트를 TTS 기능으로 음성 변환하여 NPC가 사용자에게 응답하도록 했습니다. [cite: 95, 168]

## 실행 화면 (Screenshots)

<table>
  <tr>
    <td align="center"><b>NPC와의 상호작용 및 피드백</b></td>
    <td align="center"><b>가상현실 편의점 환경</b></td>
  </tr>
  <tr>
    ![그림 4](https://github.com/user-attachments/assets/18d583bf-f73a-4550-88c2-da94a3e49a5c)
  </tr>
  <tr>
    [cite_start]<td align="center"><em>화면. 사용자의 발화에 대한 실시간 문법 교정 피드백 [cite: 173]</em></td>
  </tr>
</table>

## 사용성 평가 (Usability Evaluation)

[cite_start]저희는 개발한 시스템의 효과를 검증하기 위해, **20대 사용자 15명을 대상**으로 기존 영어 스피킹 애플리케이션과 비교하는 사용성 평가를 진행했습니다. [cite: 183] [cite_start]평가는 학습 효과와 몰입도 두 가지 측면에서 5점 척도로 이루어졌습니다. [cite: 185, 196]

### 학습 효과 (Learning Effectiveness)

* [cite_start]**영어 실력 향상 체감**: 4.93점 [cite: 201]
* [cite_start]**대화 상황에서의 유용성**: 4.53점 [cite: 202]
* [cite_start]**피드백 구체성**: 4.86점 [cite: 202]

### 몰입도 (Engagement/Immersion)

* [cite_start]**VR 환경의 생동감**: 4.6점 [cite: 218]
* [cite_start]**NPC와의 상호작용**: 4.6점 [cite: 218]
* [cite_start]**흥미와 재미**: 4.93점 [cite: 218]

[cite_start]평가 결과, 저희 시스템이 기존 학습 앱에 비해 **더 높은 학습 효과와 몰입도를 제공**할 수 있다는 긍정적인 결과를 얻었습니다. [cite: 235]

## 한계점 및 향후 과제 (Limitations & Future Work)

[cite_start]프로젝트를 진행하며 다음과 같은 **한계점**들을 발견했습니다. [cite: 247]

* [cite_start]NPC의 립싱크나 애니메이션이 없어 시각적 몰입감이 다소 제한적이었습니다. [cite: 248]
* [cite_start]초기에 설정한 프롬프트에만 기반하여 NPC가 응답하기 때문에, 장기적으로 대화의 다양성이 부족해질 수 있습니다. [cite: 249]
* [cite_start]데이터 전송에 사용한 폴링 방식으로 인해 약 6초의 지연이 발생하여, 실시간 상호작용을 다소 저해했습니다. [cite: 250]

이러한 한계점들을 개선하기 위해 다음과 같은 **향후 과제**를 계획하고 있습니다.

* [cite_start]NPC에 립싱크와 자연스러운 애니메이션을 추가하여 몰입감을 향상시키고자 합니다. [cite: 251]
* [cite_start]사용자와의 대화 데이터를 AI 모델 학습에 지속적으로 반영하여 더욱 다양하고 풍부한 대화가 가능하도록 시스템을 고도화할 것입니다. [cite: 252]
* [cite_start]실시간 상호작용 경험을 개선하기 위해 즉각적인 피드백 시스템을 도입하여 응답 지연 시간을 단축할 계획입니다. [cite: 256]
