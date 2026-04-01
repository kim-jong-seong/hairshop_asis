# 이미란헤어샵 v1.0 (ASIS)

## 개요
- 이미란헤어샵 관리 시스템 v1.0 (순수 HTML/CSS/JS 버전)
- v2.0(React 전환) 이전의 원본 코드 백업 저장소

## 기술 스택
- **프론트엔드**: HTML, CSS, JavaScript (순수 구현, 프레임워크 미사용)
- **백엔드**: Node.js + Express
- **DB**: SQLite (sqlite3)
- **이메일 백업**: Nodemailer + node-cron
- **기타**: csv-writer, jszip (데이터 내보내기)

## 프로젝트 구조
```
backend/
  server.js          - Express API 서버 (메인)
  emailBackup.js     - 이메일 자동/수동 백업
  package.json       - 의존성 정의
frontend/
  index.html         - 로그인 페이지
  dashboard.html     - 대시보드 (메인 SPA)
  css/style.css      - 전체 스타일시트
  js/login.js        - 로그인 처리
  js/dashboard.js    - 대시보드 전체 로직
  logo.png           - 로그인 페이지 로고
  logo_dash.png      - 대시보드 로고
```

## 주요 기능
- 로그인 (일반/관리자 비밀번호 분리)
- 고객 관리 (등록, 수정, 삭제)
- 시술 항목 관리 (등록, 수정, 삭제, 즐겨찾기)
- 시술 내역 관리 (등록, 수정, 삭제, 직접입력)
- 매출 현황 (일별/월별/연별 조회)
- 데이터 내보내기 (CSV ZIP 다운로드)
- DB 파일 다운로드
- 이메일 자동/수동 백업
- 관리자 SQL 직접 실행

## DB 테이블
- **customers** - 고객 (id, name, gender, phone, memo)
- **services** - 시술 항목 (id, name, price, is_favorite, is_deleted)
- **history** - 시술 내역 (id, customer_id, service_id, amount, memo, is_direct_input, modified_service_name)
- **backup_settings** - 백업 설정 (자동백업 여부, 주기, 시간, 이메일)

## API 엔드포인트
| Method | Path | 설명 |
|--------|------|------|
| POST | /api/login | 로그인 |
| GET/POST/PUT/DELETE | /api/customers | 고객 CRUD |
| GET/POST/PUT/DELETE | /api/services | 시술 항목 CRUD |
| PUT | /api/services/:id/favorite | 즐겨찾기 토글 |
| GET/POST/PUT/DELETE | /api/history | 시술 내역 CRUD |
| GET | /api/sales | 매출 통계 |
| GET | /api/export/csv | CSV 내보내기 (ZIP) |
| GET/PUT | /api/backup/settings | 백업 설정 |
| POST | /api/backup/run | 수동 백업 실행 |
| POST | /api/admin/execute-sql | SQL 직접 실행 |
| GET | /api/database/download | DB 파일 다운로드 |

## 실행 방법
```bash
cd backend
npm install
node server.js
# http://localhost:3000 접속
```
