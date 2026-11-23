# Formula-EV-Hardware-Notes (한국어 요약)
> 🌐 **Language:** [🇺🇸 English (메인 페이지)](README.md) | **🇰🇷 한국어 (Korean)**

## 📌 프로젝트 개요
본 저장소는 **Formula EV(자작전기자동차)** 파워트레인 및 안전 시스템을 위한 회로 해석, **LTspice 시뮬레이션**, 그리고 **Altium Designer** PCB 설계 과정을 기록하는 엔지니어링 노트입니다.

차량제어기(**VCU**), KSAE/FSAE 안전 규정 필수 회로(**BSPD, 프리차지 회로**), **HESS(배터리+슈퍼커패시터)** 센서 인터페이스 등 노이즈에 강한 고신뢰성 전장 회로를 직접 설계하고, 3D PCB 데이터를 **3DEXPERIENCE CATIA** 기구 하우징과 통합 검증하는 것을 목표로 합니다.

---

## 🗺️ 4단계 하드웨어 설계 로드맵

- [x] **0단계 (Phase 0):** GitHub 저장소 세팅 및 차량용 PCB 설계 규칙(DRC) 수립
- [ ] **1단계 (Phase 1): 회로 시뮬레이션 및 Altium 기초 (`01_Circuit_Sim_Basics/`)**
  - LTspice 스위칭·전원부 시뮬레이션, 커스텀 회로 심볼 및 PCB 풋프린트 라이브러리 제작
- [ ] **2단계 (Phase 2): FSAE/KSAE 안전 회로 (`02_Safety_Circuits/`)**
  - 아날로그 브레이크 신뢰성 장치(BSPD), 프리차지(Pre-charge) 및 방전 회로 설계
- [ ] **3단계 (Phase 3): VCU 및 센서 인터페이스 PCB (`03_VCU_PCB_Design/`)**
  - MCU 전원부(Buck/LDO) 노이즈 저감, 절연형 CAN 트랜시버 배치, EMI/EMC 그라운드 설계
- [ ] **4단계 (Phase 4): ECAD-MCAD 기구 통합 (`04_ECAD_MCAD_Integration/`)**
  - CATIA 방수 알루미늄 하우징과 PCB 커넥터·소자 간 3D 간섭 및 방열 패키징 검증

---

## 📂 설계 기록 및 회로 갤러리

| 번호 | 폴더 / 회로명 | 사용 툴 | 주요 설계 포인트 | 진행 상태 |
| :--- | :--- | :--- | :--- | :--- |
| **01** | `01_MOSFET_LowSide_Driver` | LTspice | 3.3V/5V MCU 신호 기반 고전류 부하 스위칭 및 게이트 링잉 트레이드오프 분석 | 🔄 진행 중 |
| **02** | `02_Power_Regulator_Test` | Altium Designer | 12V ➔ 5V/3.3V 강압(Buck/LDO) 회로 및 발열 패턴 PCB 레이아웃 | ⏳ 예정 |
| **03** | `03_BSPD_Safety_Board` | LTspice / Altium | 하드웨어 비교기 로직 및 페일세이프(Fail-safe) 셧다운 래치 구현 | ⏳ 예정 |
| **04** | `04_VCU_Main_Controller` | Altium Designer | 듀얼 CAN 통신, 센서 아날로그 필터링, 4층 기판(4-Layer PCB) 설계 | ⏳ 예정 |

---

## ⚡ 대표 회로 스터디 #01: MOSFET 로우사이드 스위칭 드라이버 설계

### 1. 설계 목표 (Objective)
* 3.3V/5V MCU 제어 신호를 이용해 냉각팬, 셧다운 릴레이 등 고전류 부하를 안전하게 구동하기 위한 MOSFET 스위칭 회로를 설계하고 시뮬레이션합니다.

### 2. 회로 구성 및 시뮬레이션 핵심 소자
* **게이트 저항 ($10\Omega$):** 돌입 전류(Inrush current)를 제한하여 MCU GPIO 핀을 보호합니다.
* **풀다운 저항 ($10\text{k}\Omega$):** MCU 핀이 플로팅(Floating) 상태일 때 의도치 않게 MOSFET이 켜지는 오작동을 방지합니다.
* **플라이백 다이오드 (Flyback Diode):** 유도성 부하(릴레이·모터 등) 차단 시 발생하는 역기전력 스파이크로부터 MOSFET을 보호합니다.

### 3. 핵심 인사이트 및 트레이드오프 (Trade-offs)
* 게이트 저항값을 낮추면 스위칭 속도가 빨라져 발열 손실이 줄어드는 반면, 저항값을 높이면 전자기적 링잉(Ringing) 노이즈가 감소하는 트레이드오프 관계를 시뮬레이션으로 검증했습니다.

---

## 🛠️ 하드웨어 문서화 규칙
* **시뮬레이션 및 레이아웃 증빙:** 완료된 모든 회로는 **LTspice** 파형 그래프(`.png`), 회로도 캡처, 2D/3D PCB 레이아웃 렌더링 이미지, 부품 리스트(**BOM**)를 함께 업로드합니다.
* **안전 규정 준수:** 고전압-저전압 간 절연 거리(Clearance & Creepage)는 **KSAE / FSAE EV** 기술 규정을 기준으로 설계합니다.

