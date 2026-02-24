[한국어](README.md) | [English](README_EN.md)

# CryptoMarket — Simulated Cryptocurrency Exchange

A real-time cryptocurrency paper trading web application.
Fetches live market data from the Upbit API and lets users trade with virtual funds, featuring real-time chat, community boards, and portfolio management.

---

## Features

### Real-Time Price Tracking
- Live market data for 10 major cryptocurrencies (BTC, ETH, XRP, DOGE, etc.) via **Upbit API**
- 500ms AJAX polling for real-time price, daily change %, and high/low updates
- Color-coded indicators: red for price increases, blue for decreases

### Candlestick Charts
- **Highcharts Stock** OHLC candlestick chart visualization
- 6 timeframes: 1-min, 5-min, 15-min, 30-min, 1-hour, daily candles
- 100 historical candles loaded from Upbit Candle API

### Paper Trading (Simulated)
- **1,000,000 KRW virtual balance** granted upon registration
- Buy: enter quantity or use preset percentages (10%, 25%, 50%, 100% of available funds)
- Sell: sell from held positions
- Real-time tracking of average purchase price, quantity held, and total investment

### Real-Time Chat
- **Spring WebSocket** broadcast chat room
- Instant message exchange between connected users

### Community Board
- Per-cryptocurrency discussion boards (full CRUD)
- **CKEditor** rich text editor support
- Like/dislike voting system with comments
- Pagination support

### User Features
- Registration / Login (standard + **Kakao OAuth** social login)
- My Page: portfolio view (holdings, current value, P&L), favorite coins list
- Coin watchlist with star-toggle favorites

### Admin Panel
- Member management (view, delete)
- News management (create, delete) — displayed as a slider on the main dashboard

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| **Language** | Java 11 |
| **Framework** | Spring Boot 2.5.5 |
| **Build** | Maven |
| **ORM** | MyBatis 2.2.0 |
| **Database** | Oracle (ojdbc8) |
| **View** | JSP + JSTL |
| **Real-time** | Spring WebSocket |
| **Frontend** | Bootstrap 3, jQuery 3.5.1 |
| **Chart** | Highcharts Stock (candlestick) |
| **Editor** | CKEditor |
| **External API** | Upbit REST API (ticker + candles) |
| **Social Login** | Kakao OAuth SDK |
| **Packaging** | WAR (external Tomcat deployment) |

---

## Supported Coins (10)

BTC, ETH, XRP, DOGE, EOS, OMG, ELF, XLM, MATIC, TRX (all KRW-paired via Upbit)

---

## Project Structure

```
SpringTeamProject/
├── pom.xml
├── src/main/java/org/coin/
│   ├── MainPageApplication.java      # Spring Boot entry point
│   ├── MainController.java           # Controller (30+ endpoints)
│   ├── ChatHandler.java              # WebSocket chat handler
│   ├── config/
│   │   └── WebSocketConfig.java      # WebSocket configuration
│   ├── dto/                          # DTOs (Member, Board, Comment, News)
│   ├── mapper/                       # MyBatis mapper interfaces
│   └── service/                      # Business logic services
├── src/main/resources/
│   ├── application.properties
│   └── mapper/                       # MyBatis XML mappers
└── src/main/webapp/
    └── WEB-INF/views/                # JSP view templates
```

---

## Getting Started

### Prerequisites
- Java 11+
- Oracle DB
- Maven

### Setup

1. Configure Oracle DB connection in `application.properties`
2. Create required tables (Member, Board, Comment, News)

### Run
```bash
git clone https://github.com/kyangkyongkyungkyang/CryptoMarket.git
cd CryptoMarket/SpringTeamProject
./mvnw spring-boot:run
```
Access at `http://localhost:9999`

---

## Project Info

- **Period**: 2021
- **Type**: Team project (vocational training course)
- **My Role**: Backend development (real-time price integration, trading logic, WebSocket chat)
