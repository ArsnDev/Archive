# 오목 게임 웹 클라이언트

실시간 멀티플레이어 오목 게임의 HTML/JavaScript 클라이언트입니다.

## 🎮 기능

### ✅ 구현 완료
- **사용자 인증**: 회원가입, 로그인, 자동 로그인
- **실시간 매칭**: 자동 플레이어 매칭 시스템
- **게임 플레이**: 19x19 오목 보드, 실시간 대전
- **서버 중심 게임 로직**: Server Authority 방식으로 안정적인 멀티플레이어 구현
- **전적 관리**: 승/패 기록, 통계 표시

### 🔧 기술 스택
- **Frontend**: HTML5, CSS3, JavaScript (ES6+)
- **UI Framework**: Bootstrap 5.1.3
- **실시간 통신**: SignalR JavaScript Client
- **API 통신**: Fetch API
- **게임 아키텍처**: Server Authority Pattern

## 📁 프로젝트 구조

```
OmokClient/
├── index.html          # 로그인/회원가입 페이지
├── game.html           # 게임 메인 화면
├── profile.html        # 프로필/전적 페이지
├── css/
│   └── style.css       # 커스텀 스타일
└── js/
    ├── api.js          # REST API 통신
    ├── auth.js         # 사용자 인증 관리
    ├── signalr.js      # SignalR 연결 관리
    ├── game.js         # 게임 로직 (Server Authority)
    └── profile.js      # 프로필 페이지 로직
```

## 🚀 GitHub Pages 배포 가능

이 클라이언트는 정적 웹사이트로 설계되어 GitHub Pages에 바로 배포할 수 있습니다.

### 배포 방법
1. 이 폴더를 GitHub 리포지토리로 생성
2. GitHub Pages 활성화
3. 서버 URL만 배포된 서버 주소로 변경

### 서버 연결 설정
`js/api.js`와 `js/signalr.js`에서 서버 URL 수정:

```javascript
// 개발환경
BASE_URL: 'http://localhost:5043/api'

// 배포환경 (예시)
BASE_URL: 'https://your-server.railway.app/api'
```

## 🔗 서버 API 연동

### REST API 엔드포인트
- `POST /api/users/register` - 회원가입
- `POST /api/users/login` - 로그인  
- `GET /api/users/me` - 내 정보 조회
- `POST /api/matchmaking/queue` - 매칭 등록
- `GET /api/matches/history/{userId}` - 전적 조회

### SignalR 이벤트 (Server Authority)
**클라이언트 → 서버:**
- `Register(userId)` - 연결 등록
- `PlaceStone(roomId, x, y)` - 돌 배치 요청

**서버 → 클라이언트:**
- `GameStateUpdate(gameState)` - 전체 게임 상태 업데이트
- `ActionResult(result)` - 액션 성공/실패 결과
- `GameOver(winnerName)` - 게임 종료

## 🏗️ Server Authority 아키텍처

이 클라이언트는 **Server Authority** 패턴을 구현합니다:

- 클라이언트는 사용자 입력을 서버로 전송만
- 서버에서 모든 게임 로직 검증 및 처리
- 서버가 전체 게임 상태를 모든 클라이언트에 브로드캐스트
- 클라이언트는 서버에서 받은 상태로만 UI 업데이트

이를 통해 치팅 방지 및 일관된 게임 상태를 보장합니다.

## 🎯 포트폴리오 활용

이 프로젝트는 다음과 같은 기술력을 보여줍니다:

- **실시간 멀티플레이어 게임** 개발 경험
- **SignalR WebSocket** 실시간 통신 구현
- **Server Authority** 게임 아키텍처 이해
- **REST API** 연동 및 JWT 인증 처리
- **Canvas 2D** 그래픽 프로그래밍
- **모듈화된 JavaScript** 아키텍처
- **GitHub Pages** 정적 웹사이트 배포

## 📝 라이선스

이 프로젝트는 학습 및 포트폴리오 목적으로 제작되었습니다.