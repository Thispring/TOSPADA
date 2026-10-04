# TOSPADA

<p align="center">
  <img src="ScreenShot/s3.jpg" width="85%" alt="TOSPADA 메인 화면">
</p>

포커 족보 규칙으로 카드를 조합하고, 완성한 족보로 상대와 승부하는 2D 카드 게임입니다.

졸업 프로젝트로, 게임 기획과 클라이언트 프로그래밍을 맡았습니다.

---

## 프로젝트 소개

플레이어는 받은 카드 중 5장을 골라 포커 족보를 만들고, 족보에 따라 생성된 유닛 카드로 상대와 승부합니다.

| 항목 | 내용 |
| --- | --- |
| 플랫폼 | PC (Windows, macOS) |
| 개발 엔진 | Unity |
| 개발 언어 | C# |
| 개발 기간 | 2023.03 ~ 2023.09 |
| 개발 인원 | 4명 (아트 3명 / 기획 · 프로그래밍 1명, 본인) |

---

## Gameplay

| 카드 조합 | 카드 전투 |
| :---: | :---: |
| <img src="ScreenShot/s2.jpg" width="100%" alt="포커 족보 카드 조합 화면"> | <img src="ScreenShot/s1.jpg" width="100%" alt="상대와의 카드 전투 화면"> |
| 카드 5장을 골라 족보를 완성하는 단계 | 완성한 족보로 상대와 승부하는 단계 |

[TOSPADA Gameplay Video](https://www.youtube.com/watch?v=RJ1uljOHJCw)

---

## Download

- [Download for Windows](https://drive.google.com/file/d/1zvfu38_7ixoJsuSYehwvt26DPWS3q7uM/view)
- [Download for macOS](https://drive.google.com/file/d/1fpbHJBM-X1aVQ4_rocC40X9PYiJJj0Vv/view)

---

## My Role

### 게임 기획

- 포커 족보를 기반으로 한 게임 규칙과 승패 구조 설계
- 카드 선택 → 족보 완성 → 유닛 카드 전투로 이어지는 플레이 흐름 기획

### 클라이언트 프로그래밍

- 카드 생성 · 배분과 카드 선택 처리
- 포커 족보 판정
- 라운드 진행(제한 시간, 전투, 결과 표시)
- UI · 사운드

---

## 주요 구현 내용

### 카드 생성과 배분

문양 4종 × 숫자 13개로 52장의 카드를 생성하고, 플레이어와 상대에게 9장씩 무작위로 나눠 줍니다. 플레이어가 고른 카드는 5칸의 선택 슬롯에 담깁니다.

**관련 코드** [Card.cs](https://github.com/Thispring/TOSPADA/blob/main/Script/Card.cs) · [Dealer.cs](https://github.com/Thispring/TOSPADA/blob/main/Script/Dealer.cs) · [Player.cs](https://github.com/Thispring/TOSPADA/blob/main/Script/Player.cs)

### 포커 족보 판정

선택 슬롯 5칸이 모두 채워지면 족보를 판정합니다.

- 카드를 숫자별로 묶고, 가장 큰 묶음의 크기로 포카드 · 풀하우스 · 트리플 · 투페어 · 원페어를 구분합니다.
- 숫자가 모두 다를 때는 로열 스트레이트 플러시, 마운틴, 스트레이트 플러시, 플러시, 스트레이트 순으로 검사합니다.

판정 결과에 따라 전투에 쓰이는 유닛 카드가 정해집니다.

**관련 코드** [PokerChecker.cs](https://github.com/Thispring/TOSPADA/blob/main/Script/PokerChecker.cs) · [UnitCard.cs](https://github.com/Thispring/TOSPADA/blob/main/Script/UnitCard.cs)

### 라운드 진행

카드 배분 → 제한 시간 안에 카드 선택 → 유닛 카드 생성 → 필드 전투 → 결과 표시 순으로 라운드가 진행됩니다.

**관련 코드** [Manager.cs](https://github.com/Thispring/TOSPADA/blob/main/Script/Manager.cs) · [Field.cs](https://github.com/Thispring/TOSPADA/blob/main/Script/Field.cs) · [Result.cs](https://github.com/Thispring/TOSPADA/blob/main/Script/Result.cs)

---

> 이 저장소는 포트폴리오 공개용으로 스크립트 코드만 포함하고 있으며, 게임 에셋과 전체 프로젝트 파일은 포함하지 않습니다.
