# ☕ Study Cafe Manager
### IoT 기반 스터디카페 좌석 예약 및 관리 시스템

> **라즈베리파이 서버와 STM32 디바이스를 연동하여  
> 좌석 상태와 환경 정보를 실시간으로 관리하는 IoT 시스템**

---

## 📌 프로젝트 개요

**Study Cafe Manager**는 스터디카페 좌석의  
**예약 / 일시정지 / 종료 상태를 실시간으로 관리**하고,  
온도·습도·소음 등 **환경 데이터까지 함께 제공하는 IoT 기반 관리 시스템**입니다.

라즈베리파이 서버와 데이터베이스를 중심으로  
STM32 디바이스, 센서 노드, 블루투스 통신을 연계하여  
**저비용·고효율 좌석 관리 솔루션**을 구현하는 것을 목표로 했습니다.

- 프로젝트 유형: IoT / Embedded System 팀 프로젝트  
- 소속: [Edge AI SW 아카데미 8기]  
- 팀: 11조 (김선곤, 김영교)

---

## 🎯 요구사항 및 목표

- 좌석 상태 실시간 확인 (OPEN / FULL / PAUSE)
- 예약 / 일시정지 / 종료 시 LCD 즉시 반영
- 환경 데이터(온도·습도·소음) 실시간 표시
- 관리자 웹(DB) 조작만으로 전체 시스템 자동 갱신
- 저비용 IoT 기술 기반 확장 가능한 구조 설계

---

## 🔍 주요 기능

### 👤 사용자 기능
- 좌석 예약 시작 / 종료
- 일시정지 및 재개
- 사용 시간 연장
- 현재 좌석 상태 확인
- 환경 데이터(온도, 습도, 소음) 확인

### 🧑‍💼 관리자 기능
- phpMyAdmin 웹 인터페이스를 통한 DB 관리
- 좌석 상태 원격 제어
- 예약 정보 수정 및 모니터링
- 시스템 상태 실시간 확인

---

## 🧠 시스템 구조

### 🔁 전체 데이터 흐름

DB(MariaDB) → Server(Raspberry Pi) → Bluetooth(HC-05) → STM32 → LCD


- DB 변경 사항을 서버가 감지
- 블루투스 브릿지를 통해 STM32로 전송
- LCD에 좌석 상태 및 환경 정보 즉시 반영

---

## 🔧 하드웨어 구성

- **STM32 Nucleo-F411RE**
  - 좌석 상태 및 환경 데이터 표시 제어
- **HC-05 Bluetooth Module**
  - 서버 ↔ STM32 무선 통신
- **LCD1602 (I2C)**
  - 좌석 상태 / 환경 정보 출력
- **ESP8266**
  - 센서 데이터 WiFi 전송
- **온습도 / 소음 센서**
  - 실시간 환경 데이터 수집
- **4×4 Keypad**
  - 좌석 예약 및 시간 제어

---

## 🗄️ DB 설계

- **reservations**
  - 좌석 예약 기록
  - 시작 / 종료 시간
  - 일시정지 상태 관리

- **env_current**
  - 온도 / 습도 / 소음 데이터
  - 최신 환경 정보 유지

- **seat_current (VIEW)**
  - 좌석 상태 계산용 뷰
  - OPEN / FULL / PAUSE 상태 제공

---

## 👨‍💻 담당 역할 (김영교)

- STM32 디바이스 제어 로직 구현
- LCD1602 출력 UI 설계
- 블루투스 통신 기반 데이터 수신 처리
- 좌석 상태 표시 로직 구현
- 서버 → 디바이스 데이터 흐름 연동
- 전체 시스템 통합 테스트 및 디버깅

---

## 📹 시연 시나리오

- 관리자 DB 예약 입력 → LCD에 즉시 FULL 표시
- 일시정지 처리 → PAUSE 상태 전환
- 예약 종료 → OPEN 상태로 복귀
- 환경 센서 값 변경 → LCD 2행 ENV 정보 실시간 갱신

---

## 🛠️ 기술 스택

### Embedded / Hardware
![STM32](https://img.shields.io/badge/STM32-03234B?style=for-the-badge&logo=stmicroelectronics)
![Raspberry Pi](https://img.shields.io/badge/Raspberry%20Pi-C51A4A?style=for-the-badge&logo=raspberrypi)
![ESP8266](https://img.shields.io/badge/ESP8266-000000?style=for-the-badge)

### Communication / DB
![Bluetooth](https://img.shields.io/badge/Bluetooth-0082FC?style=for-the-badge&logo=bluetooth)
![MariaDB](https://img.shields.io/badge/MariaDB-003545?style=for-the-badge&logo=mariadb)

### OS / Tools
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![phpMyAdmin](https://img.shields.io/badge/phpMyAdmin-6C78AF?style=for-the-badge)

---

## 🌱 기대 효과

- 좌석 운영 효율 향상 및 대기 시간 감소
- 실시간 현황 제공으로 사용자 만족도 증가
- 관리자의 유지보수 부담 최소화
- IoT 실무 경험 및 시스템 설계 역량 강화

---

## 🔮 확장 아이디어

- 다중 좌석 관리 시스템 확장
- 모바일 앱 연동
- 자동 알람 및 예약 연장 기능
- 결제 시스템 통합
- 빅데이터 기반 사용 패턴 분석
