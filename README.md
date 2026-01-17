# ⚔️ PEDemo - League of Legends Imitation

> **Unreal Engine 4.26 Blueprint**로 구현한 3D MOBA 게임 "리그 오브 레전드" 모작 프로젝트

[![Download on itch.io](https://img.shields.io/badge/Download-itch.io-FA5C5C?style=for-the-badge&logo=itch.io&logoColor=white)](https://shimwoojin.itch.io/pedemo)
[![YouTube](https://img.shields.io/badge/YouTube-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/watch?v=jydxblyq4mM&t=2s)

[![Video](https://img.youtube.com/vi/jydxblyq4mM/maxresdefault.jpg)](https://www.youtube.com/watch?v=jydxblyq4mM&t=2s)
**▶️ [YouTube 플레이 영상 보기](https://www.youtube.com/watch?v=jydxblyq4mM&t=2s)**

---

## 🎮 다운로드

### **[itch.io에서 게임 다운로드](https://shimwoojin.itch.io/pedemo)**

게임을 직접 플레이해보세요! 다운로드 후 압축 해제만 하면 바로 실행 가능합니다.

#### 💻 시스템 요구사항
- **OS**: Windows 10/11 (64-bit)
- **DirectX**: 11 이상
- **메모리**: 8GB RAM 권장
- **그래픽**: NVIDIA GTX 1050 / AMD RX 560 이상
- **저장 공간**: 2GB 이상

---

## 📋 프로젝트 개요

- **개발 기간**: 2023.04 ~ 2023.05 (2개월)
- **개발 인원**: 1인 (개인 프로젝트)
- **장르**: 3D MOBA (Multiplayer Online Battle Arena)
- **목적**: 언리얼 엔진 블루프린트 기반 게임플레이 시스템 학습

---

## 🛠 기술 스택

| 분류 | 기술 |
|------|------|
| **엔진** | Unreal Engine 4.26 |
| **개발 방식** | Blueprint (비주얼 스크립팅) |
| **AI 시스템** | Behavior Tree + Blackboard |
| **패턴** | Component-Based Architecture |

---

## ✨ 주요 구현 기능

### 1️⃣ 플레이어블 챔피언 2종
- **아리 (Ahri)**: 마법사 챔피언
  - 스킬: Q, W, E, R 총 4개 스킬 구현
  - 패시브 스킬 시스템
  
- **이즈리얼 (Ezreal)**: 원거리 챔피언
  - 투사체 기반 스킬 시스템
  - 쿨타임 관리

### 2️⃣ AI 적 시스템
- **Behavior Tree 기반 AI**
  - 패턴 기반 전투
  - 타겟 추적 및 공격
  - 상태별 행동 전환

- **적 캐릭터**: 아리, 이즈리얼 AI 버전

### 3️⃣ 스킬 시스템
- **쿨타임 관리**: `BP_CoolTimeSkill`
- **패시브 스킬**: `BP_PassiveSkill`
- **스킬 컴포넌트**: 재사용 가능한 스킬 구조

### 4️⃣ 캐릭터 선택 시스템
- 플레이어 캐릭터 선택 UI
- 적 캐릭터 선택 UI
- GameInstance를 통한 데이터 전달

### 5️⃣ UI 시스템
- **게임 HUD**: HP/MP 게이지, 스킬 쿨타임 표시
- **타이머**: 게임 진행 시간 표시
- **게임 상태**: 승/패 판정 UI
- **재시작 기능**: 게임 오버 후 재시작

---

## 🎮 조작법

| 키 | 기능 |
|---|------|
| **W, A, S, D** | 이동 |
| **Shift** | 빠른 달리기 |
| **마우스 좌클릭** | 기본 공격 |
| **Q** | 스킬 1 |
| **마우스 우클릭** | 스킬 2 |
| **E** | 스킬 3 |
| **R** | 궁극기 |

---

## 📁 프로젝트 구조

```
PEDemo/
├── Content/
│   ├── BluePrints/
│   │   ├── Actors/
│   │   │   ├── Characters/        # 캐릭터 시스템
│   │   │   │   ├── Player/        # 플레이어 아리, 이즈리얼
│   │   │   │   └── Enemy/         # AI 적 캐릭터
│   │   │   │       └── AI/        # Behavior Tree, Tasks, Services
│   │   │   ├── Skills/            # 스킬 시스템
│   │   │   │   ├── AhriSkills/
│   │   │   │   └── EzrealSkills/
│   │   │   ├── Projectiles/       # 투사체
│   │   │   └── Texts/             # 대미지 텍스트
│   │   ├── Components/            # 재사용 컴포넌트
│   │   │   ├── BP_CharacterStateComponent
│   │   │   └── BP_SkillComponent
│   │   ├── UI/                    # 게임 UI
│   │   │   ├── WBP_MainUI
│   │   │   ├── WBP_PlayerUI
│   │   │   ├── WBP_SelectPlayerCharacter
│   │   │   └── WBP_GameStateUI
│   │   ├── Datas/                 # 데이터 에셋
│   │   ├── Interfaces/            # 블루프린트 인터페이스
│   │   └── Utilities/             # 유틸리티 함수
│   ├── Maps/                      # 게임 레벨
│   │   ├── MainUI.umap           # 메인 메뉴
│   │   └── Test01~Test07.umap    # 테스트 맵
│   └── MyAssets/                  # 게임 에셋
└── Config/                        # 프로젝트 설정
```

---

## 🎯 구현 하이라이트

### 🔹 컴포넌트 기반 설계
캐릭터의 상태와 스킬을 독립적인 컴포넌트로 분리하여 재사용성 향상
- `BP_CharacterStateComponent`: HP, MP, 상태 관리
- `BP_SkillComponent`: 스킬 로직 캡슐화

### 🔹 Behavior Tree AI
- **Blackboard**: 적 캐릭터의 상태 데이터 관리
- **Tasks**: 공격, 이동, 스킬 사용 등 행동 정의
- **Services**: 주기적 상태 체크 (타겟 감지 등)

### 🔹 스킬 상속 구조
```
BP_Skill (부모)
  ├─ BP_CoolTimeSkill (쿨타임 관리)
  └─ BP_PassiveSkill (패시브)
      ├─ AhriSkills/
      └─ EzrealSkills/
```

### 🔹 데이터 기반 캐릭터 선택
GameInstance를 통해 선택한 캐릭터 정보를 레벨 간 전달

---

## 🚀 실행 방법

### 🎮 방법 1: 다운로드한 게임 플레이 (추천)

1. **[itch.io에서 다운로드](https://shimwoojin.itch.io/pedemo)**
   
2. **압축 해제**
   ```
   PEDemo-Windows.zip 압축 해제
   → PEDemo 폴더 생성됨
   ```

3. **게임 실행**
   ```
   PEDemo/PEDemo.exe 실행
   → 게임 바로 시작!
   ```

> 💡 **빠른 시작**: 다운로드 → 압축 해제 → 실행 (3단계로 끝!)

---

### 🛠 방법 2: 소스 프로젝트에서 실행 (개발자용)

#### 📦 필수 요구사항
- **Unreal Engine 4.26**
- **Windows 10/11**
- **DirectX 11** 이상

#### ⚙️ 실행 단계

1. **Epic Games Launcher**에서 Unreal Engine 4.26 설치

2. **프로젝트 열기**
   ```
   PEDemo.uproject 더블클릭
   → Unreal Editor에서 자동 실행
   ```

3. **게임 플레이**
   - 메인 레벨: `Content/Maps/MainUI.umap` 실행
   - 에디터 상단의 "플레이" 버튼 클릭
   - 또는 `Alt + P`

---

## 📚 학습 성과

### 기술적 성장
- ✅ **Unreal Engine Blueprint** 심화 활용
- ✅ **Behavior Tree AI** 구현 경험
- ✅ **컴포넌트 기반 설계** 적용
- ✅ **UI/UX 시스템** 구축
- ✅ **스킬 쿨타임 시스템** 구현

### 게임 시스템 이해
- MOBA 장르 게임플레이 메커니즘 이해
- 캐릭터 선택 → 게임 진행 → 결과 Flow 구현
- 승/패 판정 로직 구현

---

## 🎨 게임 특징

- ⚔️ **2종 플레이어블 챔피언** (아리, 이즈리얼)
- 🤖 **AI 적 캐릭터** (Behavior Tree 기반)
- 🎯 **4개 스킬 + 패시브** 시스템
- 💫 **쿨타임 관리** 및 리소스(MP) 소모
- 🖥️ **직관적인 UI** (HP/MP, 스킬 쿨타임, 타이머)
- 🔄 **재시작 시스템** (게임 오버 후 즉시 재플레이)

---

## 📌 참고사항

- 이 프로젝트는 학습 목적으로 제작되었습니다
- Unreal Engine 4.26 블루프린트 학습을 위한 개인 프로젝트입니다
- 원작 게임의 캐릭터 모델 및 애니메이션은 교육 목적으로만 사용되었습니다

---

## 📧 Contact

- **Email**: ggoggal@gmail.com
- **Portfolio**: [https://shimwoojin-portfolio.vercel.app/](https://shimwoojin-portfolio.vercel.app/)
- **GitHub**: [@shimwoojin](https://github.com/shimwoojin)

---

**Made with ❤️ by Woojin Shim** | 2023.04 ~ 2023.05
