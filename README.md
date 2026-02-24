[한국어](README.md) | [English](README_EN.md)

# CryptoMarket — 가상화폐 모의 거래소

실시간 시세 기반의 가상화폐 모의투자 웹 애플리케이션입니다.
Upbit API에서 실시간 시세를 받아와 가상 자금으로 매매를 체험할 수 있으며, 실시간 채팅, 커뮤니티 게시판, 포트폴리오 관리 기능을 제공합니다.

---

## 주요 기능

### 실시간 시세 조회
- **Upbit API** 연동으로 10개 주요 코인(BTC, ETH, XRP, DOGE 등) 실시간 시세 표시
- 500ms 간격 AJAX 폴링으로 가격, 변동률, 고가/저가 실시간 업데이트
- 상승(빨강) / 하락(파랑) 색상 구분 표시

### 캔들스틱 차트
- **Highcharts Stock** 기반 OHLC 캔들스틱 차트
- 6가지 타임프레임 지원: 1분, 5분, 15분, 30분, 1시간, 일봉
- Upbit Candle API로 100개 캔들 히스토리 로드

### 모의 거래 (Paper Trading)
- 회원가입 시 **가상 자금 100만원** 지급
- 매수: 수량 직접 입력 또는 비율 선택 (10%, 25%, 50%, 100%)
- 매도: 보유 수량 기반 매도
- 평균 매수가, 보유량, 투자금액 실시간 추적

### 실시간 채팅
- **Spring WebSocket** 기반 실시간 브로드캐스트 채팅
- 접속 중인 사용자 간 즉시 메시지 교환

### 커뮤니티 게시판
- 코인별 게시판 (게시글 CRUD)
- **CKEditor** 리치 텍스트 에디터 지원
- 좋아요/싫어요 투표 및 댓글 기능
- 페이지네이션 지원

### 사용자 기능
- 회원가입 / 로그인 (일반 + **카카오 OAuth** 소셜 로그인)
- 마이페이지: 포트폴리오 (보유 코인, 현재 가치, 수익률), 관심 코인 목록
- 관심 코인 즐겨찾기 (별표 토글)

### 관리자 기능
- 회원 관리 (조회, 삭제)
- 뉴스 관리 (작성, 삭제) — 메인 대시보드에 슬라이더 형태로 노출

---

## 기술 스택

| 분류 | 기술 |
|------|------|
| **Language** | Java 11 |
| **Framework** | Spring Boot 2.5.5 |
| **Build** | Maven |
| **ORM** | MyBatis 2.2.0 |
| **Database** | Oracle (ojdbc8) |
| **View** | JSP + JSTL |
| **Real-time** | Spring WebSocket |
| **Frontend** | Bootstrap 3, jQuery 3.5.1 |
| **Chart** | Highcharts Stock (캔들스틱) |
| **Editor** | CKEditor |
| **External API** | Upbit REST API (시세 + 캔들) |
| **Social Login** | Kakao OAuth SDK |
| **Packaging** | WAR (외부 Tomcat 배포) |

---

## 지원 코인 (10종)

| 코인 | 티커 |
|------|------|
| 비트코인 | KRW-BTC |
| 이더리움 | KRW-ETH |
| 리플 | KRW-XRP |
| 도지코인 | KRW-DOGE |
| 이오스 | KRW-EOS |
| 오미세고 | KRW-OMG |
| 엘프 | KRW-ELF |
| 스텔라루멘 | KRW-XLM |
| 폴리곤 | KRW-MATIC |
| 트론 | KRW-TRX |

---

## 프로젝트 구조

```
SpringTeamProject/
├── pom.xml
├── src/main/java/org/coin/
│   ├── MainPageApplication.java      # Spring Boot 진입점
│   ├── MainController.java           # 컨트롤러 (30+ 엔드포인트)
│   ├── ChatHandler.java              # WebSocket 채팅 핸들러
│   ├── config/
│   │   └── WebSocketConfig.java      # WebSocket 설정
│   ├── dto/                          # DTO (Member, Board, Comment, News)
│   ├── mapper/                       # MyBatis 매퍼 인터페이스
│   └── service/                      # 비즈니스 로직 서비스
├── src/main/resources/
│   ├── application.properties
│   └── mapper/                       # MyBatis XML 매퍼
└── src/main/webapp/
    └── WEB-INF/views/                # JSP 뷰 템플릿
```

---

## 실행 방법

### 사전 요구사항
- Java 11+
- Oracle DB
- Maven

### 설정

1. `application.properties`에서 Oracle DB 접속 정보 설정
2. 필요한 테이블 생성 (Member, Board, Comment, News)

### 실행
```bash
git clone https://github.com/kyangkyongkyungkyang/CryptoMarket.git
cd CryptoMarket/SpringTeamProject
./mvnw spring-boot:run
```
접속: `http://localhost:9999`

---

## 프로젝트 정보

- **개발 기간**: 2021년
- **유형**: 국비교육 과정 팀 프로젝트
- **담당 역할**: 백엔드 개발 (실시간 시세 연동, 거래 로직, WebSocket 채팅)
