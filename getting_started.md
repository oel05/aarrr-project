# 시작하기 가이드

이 프로젝트를 **혼자서** 또는 **팀원 모두가 같은 작업**을 하면서 진행하려는 분들을 위한 가이드입니다.

**이 문서의 목적:**
- ✅ HTML 문서를 어떻게 보는지
- ✅ 문서를 어떤 순서로 읽어야 하는지
- ✅ 실제로 어떻게 작업을 진행하는지
- ✅ 3주 동안 무엇을 해야 하는지

---

## 1. HTML 문서 보는 방법

### 📂 문서 목록 (총 6개)

프로젝트 폴더의 `docs/` 디렉토리에 다음 HTML 파일들이 있습니다:

```
docs/
├── getting_started.html           (시작 안내)
├── mysql_setup_guide.html           (MySQL 설치)
├── data_dictionary.html             (데이터 구조)
├── event_relationship_diagram.html  (테이블 관계)
├── data_preprocessing_guide.html    (데이터 전처리)
├── analysis_guide.html              (AARRR 분석)
└── collaboration_guide.html         (협업 방법)
```

---

### 💻 HTML 파일 여는 방법

**방법 1: 더블클릭 (가장 간단!)**
1. Finder(Mac) 또는 탐색기(Windows)에서 `docs` 폴더 열기
2. `.html` 파일을 **더블클릭**
3. 기본 브라우저(Chrome, Safari 등)에서 자동 실행

**방법 2: 브라우저에서 직접 열기**
1. Chrome이나 Safari 실행
2. `Cmd+O` (Mac) 또는 `Ctrl+O` (Windows)
3. HTML 파일 선택

---

### 📖 HTML 문서 사용 팁

**1. 목차(TOC) 활용하기**
- 모든 HTML 문서 상단에 **목차(Table of Contents)**가 있습니다
- 목차의 제목을 클릭하면 해당 섹션으로 바로 이동합니다
- 긴 문서를 빠르게 탐색할 수 있습니다

**2. 검색 기능 사용하기**
- `Cmd+F` (Mac) 또는 `Ctrl+F` (Windows)
- 키워드로 원하는 내용 빠르게 찾기
- 예: "D7 Activation", "코호트", "전환율" 등

**3. 코드 복사하기**
- SQL 코드 영역을 마우스로 드래그
- `Cmd+C` (Mac) 또는 `Ctrl+C` (Windows)로 복사
- MySQL Workbench에 붙여넣기

**4. 북마크 추가하기**
- 자주 보는 문서는 브라우저 북마크에 추가
- 빠른 접근 가능

---

## 2. 문서 읽는 순서

### 📚 추천 학습 경로

```
1단계: 환경 설정
   ↓
   mysql_setup_guide.html
   - MySQL 설치 및 데이터베이스 설정
   - 처음 한 번만 하면 됨

2단계: 데이터 이해
   ↓
   data_dictionary.html
   - 17개 테이블 구조 파악
   - 어떤 컬럼이 있는지 확인
   ↓
   event_relationship_diagram.html ⭐ 중요!
   - 테이블 간 관계 이해
   - 조인 방법 학습
   - 분석 쿼리 패턴 학습

3단계: 데이터 전처리
   ↓
   data_preprocessing_guide.html
   - 결측치, 중복, 이상치 처리
   - 분석용 쿼리 패턴 만들기

4단계: 본격 분석
   ↓
   analysis_guide.html ⭐ 메인 가이드!
   - AARRR 프레임워크 적용
   - SQL 쿼리 15개+ 작성
   - Tableau 시각화
   - 인사이트 도출

5단계: 협업 (팀 프로젝트인 경우)
   ↓
   collaboration_guide.html
   - 팀 역할 분담
   - Google Drive 관리
   - Discord 소통
```

---

## 3. 실제 작업 프로세스

### 🎯 전체 워크플로우 (3주 과정)

```
주차  │ 작업 내용                         │ 산출물
──────┼──────────────────────────────────┼────────────────────────
1주차 │ 환경 설정 + 데이터 탐색 + 전처리  │ MySQL 설정 완료
      │ - MySQL 설치                      │ 탐색 메모
      │ - 데이터 구조 파악                │ 전처리 쿼리 5개+
      │ - 테이블 관계 이해                │ 기본 CTE 패턴
      │ - 결측치/중복/이상치 체크          │
──────┼──────────────────────────────────┼────────────────────────
2주차 │ AARRR 분석 (SQL + Tableau)       │ 분석 쿼리 15개+
      │ - Acquisition/Activation 쿼리     │ CSV 파일 10개+
      │ - Retention/Revenue 쿼리         │ 대시보드 4개
      │ - CSV 추출 및 정리                │ Tableau Public 링크
      │ - Tableau 대시보드 구성           │
──────┼──────────────────────────────────┼────────────────────────
3주차 │ 인사이트 도출 + 발표 준비          │ 인사이트 보고서
      │ - 주요 발견 사항 정리             │ 발표 자료 (PPT/PDF)
      │ - 개선 제안 작성                  │ README 완성
      │ - 발표 자료 제작                  │
```

---

## 4. 주차별 상세 가이드

### 📅 1주차: 환경 설정 + 데이터 탐색 + 전처리

#### **Day 1: MySQL 설치 및 설정**

**작업 목록:**
1. [ ] `mysql_setup_guide.html` 열어서 읽기
2. [ ] MySQL 설치 (Homebrew 사용)
3. [ ] 비밀번호 `Codeit10!`로 설정
4. [ ] MySQL Workbench 설치
5. [ ] 데이터베이스 연결 테스트

**체크 포인트:**
```sql
-- MySQL Workbench에서 이 쿼리가 실행되면 성공!
SHOW DATABASES;
USE subscription_analytics;
SHOW TABLES;
```

**문제 발생 시:**
- `mysql_setup_guide.html`의 "부록: MySQL 완전 삭제 후 재설치" 참고
- 설치 과정을 처음부터 다시 시도

---

#### **Day 2-3: 데이터 구조 파악 및 테이블 관계 이해**

**작업 목록:**
1. [ ] `data_dictionary.html` 열어서 읽기
2. [ ] 17개 테이블 목록 확인
3. [ ] 각 테이블의 주요 컬럼 파악
4. [ ] 샘플 데이터 조회

**실습 쿼리:**
```sql
-- 1. 테이블 목록 보기
SHOW TABLES;

-- 2. 주요 테이블 구조 확인
DESCRIBE complete_signup;
DESCRIBE enter_lesson_page;
DESCRIBE complete_subscription;

-- 3. 샘플 데이터 보기
SELECT * FROM complete_signup LIMIT 10;
SELECT * FROM enter_lesson_page LIMIT 10;
SELECT * FROM complete_subscription LIMIT 10;

-- 4. 데이터 개수 확인
SELECT COUNT(*) FROM complete_signup;
SELECT COUNT(*) FROM enter_lesson_page;

-- 5. 데이터 기간 확인
SELECT
    MIN(DATE(client_event_time)) AS start_date,
    MAX(DATE(client_event_time)) AS end_date
FROM complete_signup;
```

**메모 작성:**
- Google Docs나 메모장에 발견한 내용 정리
- 의문점이나 궁금한 점 기록
- 예: "왜 enter_lesson_page가 제일 많지?", "start_content는 2022년 8월부터만 있네?" 등

**추가 작업:**
3. [ ] `event_relationship_diagram.html` 열어서 정독 ⭐
4. [ ] 사용자 여정 흐름 이해
5. [ ] 조인 패턴 학습

**핵심 개념:**
- ✅ 우리 데이터는 **이벤트 로그**다 (관계형 DB 아님!)
- ✅ `user_id`로만 조인 가능
- ✅ `client_event_time`으로 시간 기반 분석
- ✅ `content.id`, `lesson.id`는 이름이 없음 (ID만 있음)

---

#### **Day 4-5: 데이터 전처리 및 CTE 패턴 작성**

**작업 목록:**
1. [ ] `data_preprocessing_guide.html` 열어서 읽기
2. [ ] 결측치, 중복, 이상치 확인
3. [ ] 5개 CTE 패턴 복사해서 실행
4. [ ] 각 CTE를 `.sql` 파일로 저장

**실습 쿼리:**
```sql
-- 1. 전체 테이블 데이터 개수
SELECT 'complete_signup' AS table_name, COUNT(*) AS row_count
FROM complete_signup
UNION ALL
SELECT 'enter_lesson_page', COUNT(*) FROM enter_lesson_page
UNION ALL
SELECT 'complete_subscription', COUNT(*) FROM complete_subscription
ORDER BY row_count DESC;

-- 2. 결측치 확인 (complete_signup)
SELECT
    COUNT(*) AS total_rows,
    SUM(CASE WHEN user_id IS NULL THEN 1 ELSE 0 END) AS null_user_id,
    SUM(CASE WHEN client_event_time IS NULL THEN 1 ELSE 0 END) AS null_time,
    SUM(CASE WHEN platform IS NULL THEN 1 ELSE 0 END) AS null_platform
FROM complete_signup;

-- 3. 중복 데이터 확인
SELECT user_id, client_event_time, COUNT(*) AS dup_count
FROM complete_signup
GROUP BY user_id, client_event_time
HAVING COUNT(*) > 1
LIMIT 10;

-- 4. 미래 날짜 확인
SELECT COUNT(*) AS future_records
FROM complete_signup
WHERE client_event_time > NOW();
```

**저장할 파일 목록:**
```
queries/
├── clean_signup.sql              (전처리된 가입 데이터)
├── clean_subscription.sql        (전처리된 구독 데이터)
├── user_first_signup.sql         (사용자별 첫 가입일)
├── user_first_payment.sql        (사용자별 첫 결제일)
└── user_activity_summary.sql     (통합 활동 요약) ⭐ 핵심!
```

💡 **중요:** `user_activity_summary.sql` 파일은 2주차에 계속 사용합니다!

---

### 📅 2주차: AARRR 분석 (SQL + Tableau)

#### **전체 목표: 분석 쿼리 15개 + 대시보드 4개**

**작업 목록:**
1. [ ] `analysis_guide.html`의 "Step 3: SQL 쿼리로 데이터 분석" 읽기
2. [ ] Q1~Q16까지 쿼리 복사해서 실행
3. [ ] 각 쿼리를 `.sql` 파일로 저장
4. [ ] 결과를 CSV로 추출

---

### 📅 5주차: 인사이트 도출 + 발표 준비

#### **Day 1-2: 데이터 분석 결과 정리**

**작업 목록:**
1. [ ] SQL 결과 + Tableau 차트 보면서 패턴 찾기
2. [ ] 이상한 점, 흥미로운 점 메모
3. [ ] 수치를 표로 정리

**예시 메모:**
```
발견 사항:
- 주말에 가입자가 평일보다 40% 적음
- iOS 사용자가 Android보다 전환율 2배 높음
- D7 활성화율 45%인데, D30은 25%로 급감
- Churn Rate가 3개월차부터 증가

의문점:
- 왜 주말에 가입자가 적을까? → 광고 문제?
- iOS 전환율이 높은 이유? → 사용자 특성? 앱 품질?
```

---

#### **Day 3-4: 인사이트 도출 및 개선 제안**

**작업 목록:**
1. [ ] `analysis_guide.html`의 "Step 5: 인사이트 도출" 읽기
2. [ ] 인사이트 템플릿 복사
3. [ ] 주요 발견 사항 3개 이상 작성
4. [ ] 개선 제안 5개 이상 작성

**인사이트 프레임워크:**
```
1. 현황 정리
   - "X 지표는 Y%입니다"

2. 문제 발견
   - "하지만 Z 구간에서 급감합니다"

3. 원인 분석
   - "이는 ~때문으로 추정됩니다"

4. 개선 제안
   - "~를 개선하면 W% 증가할 것으로 예상됩니다"
```

---

#### **Day 5-7: 발표 자료 제작**

**작업 목록:**
1. [ ] PPT 또는 Google Slides 준비
2. [ ] 발표 구조 잡기
3. [ ] Tableau 스크린샷 추가
4. [ ] 인사이트 정리
5. [ ] 리허설

**발표 구조 (10분 기준):**
```
1. 프로젝트 소개 (1분)
   - 데이터 설명
   - 분석 목표

2. AARRR 프레임워크 소개 (1분)
   - 각 단계 간단히 설명

3. 주요 발견 사항 (4분)
   - Acquisition: ~
   - Activation: ~
   - Retention: ~
   - Revenue: ~
   - 각 단계별 Tableau 차트 보여주기

4. 핵심 인사이트 (3분)
   - 발견 사항 1
   - 발견 사항 2
   - 발견 사항 3

5. 개선 제안 및 마무리 (1분)
   - 액션 아이템 5개
   - Q&A
```

---

## 5. 자주 묻는 질문 (FAQ)

---

### Q1. 쿼리가 너무 오래 걸려요 (10분 이상)

**A:** 해결 방법:
1. `LIMIT 1000` 추가해서 샘플만 테스트
2. `WHERE` 절로 날짜 범위 제한
3. 필요한 컬럼만 SELECT (SELECT * 피하기)

```sql
-- ❌ 느린 쿼리
SELECT *
FROM enter_lesson_page;

-- ✅ 빠른 쿼리
SELECT user_id, DATE(client_event_time) AS date
FROM enter_lesson_page
WHERE client_event_time >= '2024-01-01'
LIMIT 10000;
```

---

### Q2. 인사이트가 잘 안 떠올라요

**A:** 팁:
1. **비교하기**: 플랫폼별, 국가별, 시간대별 차이 찾기
2. **이상치 찾기**: 평균에서 크게 벗어난 값
3. **트렌드 보기**: 시간에 따라 증가/감소하는 패턴
4. **"왜?"라고 질문하기**: 수치 뒤에 숨은 이유 찾기

---

## 6. 체크리스트

### ✅ 주차별 완료 체크리스트

**1주차: 환경 설정 + 데이터 탐색 + 전처리**
- [ ] MySQL 설치 및 데이터베이스 연결 완료
- [ ] 17개 테이블 구조 파악
- [ ] `event_relationship_diagram.html` 정독
- [ ] 데이터 품질 진단 완료 (결측치, 중복, 이상치)
- [ ] 5개 CTE 패턴 작성 및 `.sql` 파일로 저장
- [ ] `user_activity_summary.sql` 테스트 완료

**2주차: AARRR 분석 (SQL + Tableau)**
- [ ] 분석 쿼리 15개 이상 작성
- [ ] CSV 파일 10개 이상 추출
- [ ] Tableau Desktop 설치
- [ ] 대시보드 4개 완성
- [ ] Tableau Public 게시 완료

**3주차: 인사이트 도출 + 발표 준비**
- [ ] 주요 발견 사항 3개 이상 도출
- [ ] 개선 제안 5개 이상 작성
- [ ] 발표 자료 완성
- [ ] 발표 리허설 완료

---

## 7. 프로젝트 완료 기준

### ✅ 최종 산출물 목록

**1. SQL 파일 (15개+)**
```
queries/
├── 01_acquisition/
│   ├── daily_signups.sql
│   ├── monthly_signups.sql
│   ├── platform_distribution.sql
│   └── country_top10.sql
├── 02_activation/
│   ├── time_to_first_content.sql
│   └── d7_activation_rate.sql
├── 03_retention/
│   ├── retention_rates.sql
│   ├── cohort_retention.sql
│   └── wau_mau.sql
└── 04_revenue/
    ├── conversion_rate.sql
    ├── renewal_rate.sql
    ├── churn_rate.sql
    └── arpu.sql
```

**2. CSV 파일 (10개+)**
```
results/
├── daily_signups.csv
├── platform_distribution.csv
├── d7_activation_rate.csv
├── cohort_retention.csv
├── conversion_rate.csv
└── ...
```

**3. Tableau 대시보드 (4개)**
- Executive Summary
- AARRR Funnel
- Retention Analysis
- Revenue Analysis
- Tableau Public 게시 링크

**4. 인사이트 보고서**
- 주요 발견 사항 3개 이상
- 개선 제안 5개 이상
- 액션 아이템

**5. 발표 자료**
- PPT 또는 Google Slides
- 10분 발표 분량

---

## 8. 도움말 및 참고 자료

### 🔗 유용한 링크

**MySQL 학습:**
- MySQL 공식 문서: https://dev.mysql.com/doc/
- W3Schools SQL 튜토리얼: https://www.w3schools.com/sql/

**Tableau 학습:**
- Tableau 공식 튜토리얼: https://www.tableau.com/learn/training
- Tableau Public 갤러리: https://public.tableau.com/gallery/

**AARRR 프레임워크:**
- Dave McClure의 원문: "Startup Metrics for Pirates" (검색)

---

## 9. 이 프로젝트를 통해 얻게 될 것

**기술 역량:**
- ✅ MySQL 실무 쿼리 작성 능력
- ✅ 대용량 데이터 처리 경험
- ✅ Tableau 시각화 능력
- ✅ 데이터 기반 의사결정 능력

**포트폴리오:**
- ✅ 실무 중심의 AARRR 분석 프로젝트
- ✅ Tableau Public 대시보드
- ✅ 15개 이상의 SQL 쿼리 샘플
- ✅ 인사이트 도출 및 개선 제안 능력

**분석 사고력:**
- ✅ 비즈니스 문제를 데이터로 접근
- ✅ 수치 뒤의 의미 파악
- ✅ 액션 아이템 도출 능력

---

### 💪 시작할 준비가 되셨나요?

**첫 걸음:**
1. `mysql_setup_guide.html` 열기
2. MySQL 설치 시작
3. 한 단계씩 천천히 진행

**기억하세요:**
- 처음에는 어렵지만, 계속하면 익숙해집니다
- 막히면 언제든 도움을 요청하세요
- 완벽하지 않아도 괜찮습니다. 완료하는 것이 중요합니다!


### 📞 문의 및 질문

**막히는 부분이 있다면:**
1. 해당 HTML 문서를 다시 정독
2. Discord 채널에 질문 올리기
3. 멘토/강사에게 질문
4. Google 검색

---

## 부록: 폴더 구조 예시

```
sub_analytics/
├── queries/                    (SQL 파일 저장)
│   ├── base/
│   │   ├── clean_signup.sql
│   │   ├── clean_subscription.sql
│   │   ├── user_first_signup.sql
│   │   ├── user_first_payment.sql
│   │   └── user_activity_summary.sql
│   ├── 01_acquisition/
│   ├── 02_activation/
│   ├── 03_retention/
│   └── 04_revenue/
├── results/                    (CSV 파일 저장)
│   ├── daily_signups.csv
│   ├── platform_distribution.csv
│   └── ...
├── tableau/                    (Tableau 파일)
│   ├── dashboard_v1.twbx
│   └── screenshots/
├── docs/                       (분석 문서)
│   ├── insights.md
│   └── presentation.pdf
└── README.md                   (프로젝트 소개)
```

이 구조로 폴더를 만들어두면 파일 관리가 편리합니다!

#### **Day 1-3: SQL 분석 쿼리 작성 (AARRR)**

**쿼리 목록 (15개):**

**Acquisition (4개):**
- [ ] Q1: 일별 신규 가입자 수
- [ ] Q2: 월별 신규 가입자 추이
- [ ] Q3: 플랫폼별 가입자 분포
- [ ] Q4: 국가별 가입자 Top 10

**Activation (2개):**
- [ ] Q5: 가입 후 첫 콘텐츠 시작까지 걸린 시간
- [ ] Q6: D7 Activation Rate

**Retention (3개):**
- [ ] Q7: D1/D7/D30 Retention Rate
- [ ] Q8: 월별 코호트 리텐션
- [ ] Q9: WAU/MAU

**Revenue (5개):**
- [ ] Q10: 무료→유료 전환율
- [ ] Q11: 가입 후 결제까지 걸린 시간
- [ ] Q12: 구독 갱신율
- [ ] Q13: 월별 Churn Rate
- [ ] Q14: ARPU

**CSV 추출:**
- MySQL Workbench에서 결과 그리드 우클릭 → "Export Recordset..."
- 10개+ CSV 파일 생성

---

#### **Day 4-7: Tableau 시각화 (대시보드 4개)**

**작업 순서:**
1. [ ] Tableau Desktop 설치 (학생 무료 라이선스)
2. [ ] CSV 파일들을 Tableau에 불러오기
3. [ ] 대시보드 4개 구성
4. [ ] Tableau Public에 게시

**대시보드 목록:**
- **Dashboard 1**: Executive Summary (KPI, 가입자 추이, 플랫폼 분포)
- **Dashboard 2**: AARRR Funnel (전환 퍼널, 단계별 전환율)
- **Dashboard 3**: Retention Analysis (코호트 히트맵, 리텐션 추이)
- **Dashboard 4**: Revenue Analysis (매출 추이, Churn Rate, ARPU)

**참고:** `analysis_guide.html`의 "Step 4: Tableau 시각화" 참조

---

### 📅 3주차: 인사이트 도출 + 발표 준비

---

**🔥 Shift+Enter에 마음을 불태워, 에러를 넘어 인사이트까지🚀**
