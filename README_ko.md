# OpenRobot ST-Link Tool

> **[English](README.md)** | 한국어

OpenRobot 모터 제어기(STM32F405) 양산 도구. 버튼 한 번으로 SWD 로 부트로더와 펌웨어를 굽고, CAN 으로
검사와 캘리브레이션을 진행하고, 유닛마다 PDF 성적서를 남김.

## 다운로드

**[Releases](https://github.com/dongilc/openrobot-stlink-tool/releases/latest)** 에서 최신판:

- **Windows**: `OpenRobot_STLink_Tool_v1.5.zip`

압축을 풀고 `OpenRobot_STLink_Tool_v1.5.exe` 실행. 설치 불필요. OpenOCD 가 내장되어 있고,
제품별 양산 펌웨어는 프로그램 옆 `production_fw` 폴더에 들어 있음.

## 기능

- **양산 탭**: 굽기(부트로더 + 앱 + EEPROM 소거), 연결, 상태 점검, 모터 설정, 권선 R/L, 모터 NTC,
  엔코더 오프셋, FOC 무부하 품질, 출력 엔코더 캘리브레이션과 검증, 정격/무부하 속도, 토크 리플,
  관성 튜닝과 위치 루프 주파수 응답, 출력단 백래시. 제품에 없는 단계는 건너뜀.
- **굽기 전 펌웨어 확인**: ELF 에 들어 있는 보드 이름과 `manifest.txt` 의 sha256 이 선택한 제품과 맞아야 시작함.
- **성적서**: 유닛별 PDF 와 CSV 기록, 프로그램 옆 `[성적서]` 폴더.
- **디버그 탭**: SWD 로 리셋 없이 변수 감시, 상태 점검, 스레드, 주변장치 확인.

## v1.5 포함 제품

| 제품 폴더 | 모델 |
|---|---|
| `SPN-MC_V2` | GIM8108, RMD-X6-6, SDD09-PS6 / PS8 / PS9 |
| `SPN-MC_D17_D20` | FL7016, GIM8108 |
| `VESCAT_HIGH_V2R3` / `VESCAT_HIGH_V2R4` | RV10C_27, RV6E_43 |
| `SPN-MC_D14` | 펌웨어와 부트로더만 |

## 요구 사항

- **OS**: Windows 10/11 (64-bit)
- **ST-Link V2 또는 V3** (SWD). 인식되지 않으면 ST-Link USB 드라이버(STSW-LINK009) 설치.
- **USB-CAN 어댑터**: PCAN-USB (PEAK 드라이버) 또는 CANable 2.0 (slcan). 기본 `PCAN_USBBUS1`, 1 Mbps.

## 빠른 시작

1. `OpenRobot_STLink_Tool_v1.5.zip` 다운로드 후 압축 해제.
2. 보드에 ST-Link(SWD)와 CAN 어댑터 연결, 보드 전원 인가.
3. exe 실행, 양산 탭에서 제품과 모델 선택 후 시작.

> 5단계부터 모터가 돎. 시작 전에 축 주변을 비우고 고정 상태와 전원을 확인할 것.
> 출력축 고정은 15단계(백래시)에서만 필요함.

## 라이선스

독점 소프트웨어 — [LICENSE](LICENSE) 참고. `production_fw` 의 펌웨어는 VESC 기반 GPLv3 이며,
대응 소스는 요청 시 제공함.
