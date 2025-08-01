# KBO 프로젝트 파일 구조

## 📁 핵심 파일들 (Active Files)

### 데이터 파일
- **`2025-season-data.txt`** - 원본 KBO 경기 데이터 (복잡한 형식)
- **`raw-data-analysis.json`** - 완전히 파싱된 최종 raw 데이터 (495경기, 무승부 포함)
- **`kbo-records.json`** - KBO 팀 순위 및 기록 데이터
- **`correct-kbo-data.json`** - 수정된 KBO 데이터

### 분석/파싱 스크립트
- **`parse-raw-data.js`** - 🎯 **메인 파서** - 원본 데이터를 완전히 파싱 (495경기)
- **`kbo-records.js`** - KBO 기록 계산 스크립트

### 자동화/크롤링 스크립트
- **`complete-kbo-automation.js`** - 🎯 **메인 자동화** - KBO 데이터 자동 크롤링
- **`enhanced-kbo-crawler.js`** - 향상된 KBO 크롤러
- **`kbo-official-crawler.js`** - KBO 공식 사이트 크롤러
- **`automation-status-check.js`** - 자동화 상태 체크
- **`integrate-season-data.js`** - 시즌 데이터 통합

### 배치/스케줄링
- **`auto-update.sh`** - 자동 업데이트 스크립트
- **`daily-update.sh`** - 일일 업데이트 스크립트
- **`automation-manager.sh`** - 자동화 매니저
- **`setup-cron.sh`** - 크론 작업 설정
- **`kbo_cron_jobs.txt`** - 크론 작업 설정

### 웹 인터페이스
- **`magic-number/`** - 매직넘버 계산 웹사이트
  - `index.html` - 메인 웹페이지
  - `kbo-rankings.json` - 순위 데이터
  - `manifest.json`, `robots.txt`, `sitemap.xml` - 웹 설정

### 스크립트 디렉토리
- **`scripts/`**
  - `calculate-magic-numbers.js` - 매직넘버 계산
  - `crawl-kbo-data.js` - 데이터 크롤링
  - `simple-update.js` - 간단 업데이트
  - `update-html.js` - HTML 업데이트

### 데이터 디렉토리
- **`data/`**
  - `home-away-records.json` - 홈/원정 기록
  - `last-update-date.json` - 마지막 업데이트 날짜

### 설정 파일
- **`package.json`** - Node.js 프로젝트 설정
- **`README.md`** - 프로젝트 설명
- **`AUTOMATION_GUIDE.md`** - 자동화 가이드

## 📁 보관 디렉토리

### deprecated/
구버전이거나 더 이상 사용하지 않는 파일들:
- `analyze-season-data.js` - 구버전 분석기 (108경기만 파싱)
- `analyze-new-season-data.js` - 다른 형식용 분석기
- `season-data-analysis.json` - 불완전한 분석 결과
- `2025-season-data-clean.txt` - 불완전한 정제 데이터
- 기타 구버전 파싱/크롤링 스크립트들

### archive/
테스트 파일 및 디버그 자료:
- `test-*.js` - 각종 테스트 스크립트들
- `debug-*.html` - 디버그 HTML 파일들
- `*.png` - 스크린샷 및 디버그 이미지들

## 🎯 주요 워크플로우

### 1. 데이터 파싱
```bash
node parse-raw-data.js
```
→ `2025-season-data.txt` → `raw-data-analysis.json`

### 2. 자동화 실행
```bash
node complete-kbo-automation.js
```
→ KBO 사이트 크롤링 → 데이터 업데이트

### 3. 매직넘버 계산
```bash
node scripts/calculate-magic-numbers.js
```
→ 순위 기반 매직넘버 계산

## ⚠️ 파일 참조 주의사항

- **메인 파서:** `parse-raw-data.js` 사용 (다른 파서들은 deprecated)
- **메인 데이터:** `raw-data-analysis.json` 사용 (495경기 완전 데이터)
- **자동화:** `complete-kbo-automation.js` 사용
- **구버전 파일들은 deprecated/ 폴더에 보관됨**

## 📊 데이터 정확도

- **총 경기수:** 495경기 (정규시즌 3/22~7/31)
- **무승부:** 17경기 모두 포함
- **정확도:** KBO 공식 데이터와 100% 일치
- **한화 기록:** 59승 37패 3무 (KBO 공식과 동일)