# MySQL 데이터베이스 설정 가이드 (초간단 버전)

## 📌 시작하기 전에

**MySQL 비밀번호 (모두 동일하게 사용):**
```
root 비밀번호: Codeit10!
```

**데이터베이스 이름:**
```
sub_analytics
```

💡 이 두 가지만 기억하면 됩니다!

---

## 목차
1. [MySQL 설치하기](#1-mysql-설치하기)
2. [데이터베이스 생성 및 데이터 적재하기](#2-데이터베이스-생성-및-데이터-적재하기)
3. [데이터 확인하기](#3-데이터-확인하기)
4. [SQL 쿼리 실행하기](#4-sql-쿼리-실행하기)
5. [문제 해결](#5-문제-해결)

---

## 1. MySQL 설치하기

### Mac 사용자

**터미널 열고 다음 명령어 실행:**

```bash
# MySQL 설치
brew install mysql

# MySQL 시작
brew services start mysql

# MySQL 비밀번호 설정
mysql -u root
# MySQL 프롬프트에서:
ALTER USER 'root'@'localhost' IDENTIFIED BY 'Codeit10!';
FLUSH PRIVILEGES;
EXIT;

# MySQL Workbench 설치 (GUI 도구)
brew install --cask mysqlworkbench
```

💡 **중요**: Mac도 반드시 비밀번호 `Codeit10!`을 설정하세요!

### Windows 사용자

**Step 1: MySQL 설치**
1. https://dev.mysql.com/downloads/mysql/ 접속
2. "Windows (x86, 64-bit), MSI Installer" 다운로드
3. 설치 실행
4. **중요**: root 비밀번호 설정
   - 비밀번호: **`Codeit10!`** (모두 동일하게 사용)
   - 꼭 기억하세요!

**Step 2: MySQL Workbench 설치**
1. https://dev.mysql.com/downloads/workbench/ 접속
2. 다운로드 및 설치

---

## 2. 데이터베이스 생성 및 데이터 적재하기

### 📌 시작하기 전에: 프로젝트 폴더 구조 이해하기

**⭐ 매우 중요: 이 부분을 꼭 읽어주세요!**

데이터 적재를 실패하는 가장 큰 이유는 **"어디에서 명령어를 실행하는가"**를 모르기 때문입니다.

---

#### 1️⃣ 프로젝트 폴더 만들기

**권장 위치: Documents 폴더**

먼저 Documents 폴더에 프로젝트 폴더를 만듭니다:

**Mac:**
```bash
cd ~/Documents
mkdir sub_analytics
```

**Windows:**
```cmd
cd C:\Users\내이름\Documents
mkdir sub_analytics
```

**폴더 이름은 자유롭게 정하세요!**
- `sub_analytics` (추천)
- `구독서비스_분석`
- `data_project` 등

💡 **중요**: 폴더 이름에 **띄어쓰기는 피하세요!** (명령어 실행이 복잡해집니다)

---

#### 2️⃣ 프로젝트 폴더 구조

프로젝트 폴더를 만든 후, 최소한 이 구조가 필요합니다:

```
📁 Documents
  └─ 📁 sub_analytics  👈 프로젝트 최상위 폴더 (이름은 자유)
      └─ 📁 datas  👈 이 폴더를 만들고 SQL 파일을 넣으세요!
          └─ 📁 주제 2. 구독서비스 프로덕트 데이터 분석
              └─ 📄 DAproject_middle1_topic2_dump.sql  👈 이 파일을 적재할 거예요!
```

**실제 경로 예시:**
- **Mac**: `/Users/내이름/Documents/sub_analytics`
- **Windows**: `C:\Users\내이름\Documents\sub_analytics`

---

#### 3️⃣ datas 폴더에 SQL 파일 넣기

**Step 1: datas 폴더 만들기**

**Mac:**
```bash
cd ~/Documents/sub_analytics
mkdir datas
```

**Windows:**
```cmd
cd C:\Users\내이름\Documents\sub_analytics
mkdir datas
```

**Step 2: SQL 파일이 있는 폴더를 datas 안으로 복사**

**"주제 2. 구독서비스 프로덕트 데이터 분석"** 폴더 전체를 `datas` 폴더 안에 넣으세요!

복사 후 구조:
```
sub_analytics/
└── datas/
    └── 주제 2. 구독서비스 프로덕트 데이터 분석/
        └── DAproject_middle1_topic2_dump.sql
```

**확인 방법:**

**Mac:**
```bash
ls datas/
```
결과: `주제 2. 구독서비스 프로덕트 데이터 분석` 폴더가 보여야 합니다!

**Windows:**
```cmd
dir datas\
```
결과: `주제 2. 구독서비스 프로덕트 데이터 분석` 폴더가 보여야 합니다!

---

#### 4️⃣ "프로젝트 폴더로 이동한다"는 무슨 뜻인가요?

터미널/명령 프롬프트는 **항상 어떤 위치(폴더)에서 실행**됩니다.

**현재 위치 확인 방법:**

**Mac (터미널):**
```bash
pwd
# 결과 예: /Users/yongha/Documents
```

**Windows (명령 프롬프트):**
```cmd
cd
```
결과 예: `C:\Users\yongha\Documents`

---

#### 5️⃣ 프로젝트 폴더로 이동하기

**Mac:**
```bash
cd ~/Documents/sub_analytics
```

제대로 이동했는지 확인:
```bash
pwd
```
결과: `/Users/내이름/Documents/sub_analytics`

프로젝트 폴더 내용 확인:
```bash
ls
```
결과: `datas` 폴더가 보여야 합니다!

**Windows:**
```cmd
cd C:\Users\내이름\Documents\sub_analytics
```

제대로 이동했는지 확인:
```cmd
cd
```
결과: `C:\Users\내이름\Documents\sub_analytics`

프로젝트 폴더 내용 확인:
```cmd
dir
```
결과: `datas` 폴더가 보여야 합니다!

---

#### 6️⃣ SQL 파일 경로 이해하기

프로젝트 폴더(`sub_analytics`)에서 SQL 파일까지의 **상대 경로**:

**Mac/Linux:**
```
datas/주제 2. 구독서비스 프로덕트 데이터 분석/DAproject_middle1_topic2_dump.sql
```

**Windows:**
```
datas\주제 2. 구독서비스 프로덕트 데이터 분석\DAproject_middle1_topic2_dump.sql
```

**상대 경로란?**
- **현재 위치(sub_analytics)를 기준**으로 하는 경로
- `sub_analytics` 폴더 안에 있을 때만 사용 가능!

**절대 경로 예시:**
- **Mac**: `/Users/내이름/Documents/sub_analytics/datas/주제 2. 구독서비스 프로덕트 데이터 분석/DAproject_middle1_topic2_dump.sql`
- **Windows**: `C:\Users\내이름\Documents\sub_analytics\datas\주제 2. 구독서비스 프로덕트 데이터 분석\DAproject_middle1_topic2_dump.sql`

---

#### 7️⃣ 핵심 포인트 정리

✅ **반드시 프로젝트 폴더(`sub_analytics`) 안에서 명령어를 실행하세요!**

❌ **잘못된 예:**
```bash
# 홈 폴더에서 실행 (X)
cd ~
mysql -u root -p ... < "datas/..."  # 에러 발생!
```

✅ **올바른 예:**
```bash
# 프로젝트 폴더로 먼저 이동! (O)
cd ~/Documents/sub_analytics
mysql -u root -p ... < "datas/..."  # 성공!
```

---

### 📌 전체 과정 한눈에 보기

1. **프로젝트 폴더 만들기** (Documents/sub_analytics)
2. **datas 폴더 만들고 SQL 파일 넣기**
3. **프로젝트 폴더로 이동**
4. **MySQL에서 데이터베이스 생성** (sub_analytics)
5. **SQL dump 파일 적재** → 17개 테이블 자동 생성 + 데이터 삽입
6. **완료!**

---

### ⭐ 준비된 SQL dump 파일

**Mac/Linux 경로:**
```
datas/주제 2. 구독서비스 프로덕트 데이터 분석/DAproject_middle1_topic2_dump.sql
```

**Windows 경로:**
```
datas\주제 2. 구독서비스 프로덕트 데이터 분석\DAproject_middle1_topic2_dump.sql
```

**이 파일 하나에 모든 게 들어있어요!**
- ✅ 17개 테이블 생성 명령어
- ✅ 모든 데이터 (7GB!)
- ✅ 그냥 실행만 하면 자동으로 다 됩니다!

---

### 데이터 적재 방법: 터미널/명령 프롬프트 사용

**⭐ 중요: MySQL Workbench로는 이 데이터를 적재할 수 없습니다!**

- 7GB의 대용량 데이터와 한글 인코딩 때문에 Workbench에서 오류가 발생합니다
- **반드시 터미널/명령 프롬프트를 사용**하세요!

**이 방법의 장점:**

- ✅ 인코딩 에러 없음
- ✅ 빠르고 안정적
- ✅ 진행 상황을 볼 수 있음

---

**Mac 사용자 (터미널):**

**Step 1: 터미널 열고 프로젝트 폴더로 이동**

```bash
cd ~/Documents/sub_analytics
```

제대로 이동했는지 확인:
```bash
pwd
```
결과: `/Users/내이름/Documents/sub_analytics`

프로젝트 폴더 내용 확인 (datas 폴더가 보여야 함!):
```bash
ls
```
결과: `datas`

💡 **중요**: `datas` 폴더가 안 보이면 잘못된 위치입니다! 다시 확인하세요.

---

**Step 2: 데이터베이스 생성**

MySQL 접속:
```bash
mysql -u root -p
```
비밀번호 입력: `Codeit10!`

MySQL 프롬프트(`mysql>`)가 나타나면 다음 명령어 실행:
```sql
CREATE DATABASE sub_analytics CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
EXIT;
```

성공하면 다음과 같이 표시됩니다:
```
Query OK, 1 row affected (0.01 sec)
```

---

**Step 3: SQL dump 파일 적재 (⭐ 중요!)**

**다시 확인: 현재 위치가 프로젝트 폴더인지 확인!**
```bash
pwd
```
결과: `/Users/내이름/Documents/sub_analytics` 이어야 합니다!

데이터 적재 명령어 실행:
```bash
mysql -u root -p --default-character-set=utf8mb4 sub_analytics < "datas/주제 2. 구독서비스 프로덕트 데이터 분석/DAproject_middle1_topic2_dump.sql"
```
비밀번호 입력: `Codeit10!`

**중요:**
- 비밀번호 입력 후 **아무 화면도 안 나오는 게 정상**입니다!
- 5-10분 정도 기다리면 자동으로 완료됩니다
- 터미널 프롬프트(`$` 또는 `%`)가 다시 나타나면 완료!

**만약 "No such file or directory" 에러가 나면?**
→ 프로젝트 폴더가 아닌 다른 곳에서 명령어를 실행한 것입니다!
→ **Step 1**로 돌아가서 `cd ~/Documents/sub_analytics` 실행!

---

**Windows 사용자 (명령 프롬프트):**

**Step 1: 명령 프롬프트 열고 프로젝트 폴더로 이동**

**💡 먼저 내 사용자 이름 확인:**
```cmd
echo %USERNAME%
```
결과 예: `kimcoding` (이게 당신의 사용자 이름입니다)

프로젝트 폴더로 이동:
```cmd
cd C:\Users\kimcoding\Documents\sub_analytics
```
(위에서 확인한 사용자 이름으로 `kimcoding` 부분을 바꾸세요!)

제대로 이동했는지 확인:
```cmd
cd
```
결과: `C:\Users\kimcoding\Documents\sub_analytics`

프로젝트 폴더 내용 확인 (datas 폴더가 보여야 함!):
```cmd
dir
```
결과: `datas` 폴더가 보여야 합니다!

💡 **중요**: `datas` 폴더가 안 보이면 잘못된 위치입니다! 다시 확인하세요.

---

**Step 2: 데이터베이스 생성**

MySQL 접속:
```cmd
mysql -u root -p
```
비밀번호 입력: `Codeit10!`

MySQL 프롬프트(`mysql>`)가 나타나면 다음 명령어 실행:
```sql
CREATE DATABASE sub_analytics CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
EXIT;
```

성공하면 다음과 같이 표시됩니다:
```
Query OK, 1 row affected (0.01 sec)
```

---

**Step 3: SQL dump 파일 적재 (⭐ 중요!)**

**다시 확인: 현재 위치가 프로젝트 폴더인지 확인!**
```cmd
cd
```
결과: `C:\Users\내이름\Documents\sub_analytics` 이어야 합니다!

데이터 적재 명령어 실행:
```cmd
mysql -u root -p --default-character-set=utf8mb4 sub_analytics < "datas\주제 2. 구독서비스 프로덕트 데이터 분석\DAproject_middle1_topic2_dump.sql"
```
비밀번호 입력: `Codeit10!`

**중요:**
- 비밀번호 입력 후 **아무 화면도 안 나오는 게 정상**입니다!
- 5-10분 정도 기다리면 자동으로 완료됩니다
- 명령 프롬프트(`C:\...>`)가 다시 나타나면 완료!

**만약 "No such file or directory" 에러가 나면?**
→ 프로젝트 폴더가 아닌 다른 곳에서 명령어를 실행한 것입니다!
→ **Step 1**로 돌아가서 `cd C:\Users\내이름\Documents\sub_analytics` 실행!

---

**💡 중요 옵션 설명:**
- `--default-character-set=utf8mb4`: 한글 인코딩 문제 해결
  - ⚠️ **주의**: `utf8mb4`가 맞습니다! (`utf8m4` 아님, b가 있어야 함!)
- `sub_analytics`: 적재할 데이터베이스 이름 지정
- 비밀번호 입력 후 5-10분 기다리면 완료!

---

### ✅ 적재 완료 확인하기

터미널/명령 프롬프트에서 다음 명령어로 확인:

```bash
# MySQL 접속
mysql -u root -p
# 비밀번호 입력: Codeit10!
```

MySQL 프롬프트(mysql>)에서:
```sql
-- 데이터베이스 목록 확인
SHOW DATABASES;
```

다음과 같이 `sub_analytics`가 보이면 성공!
```
+------------------------+
| Database               |
+------------------------+
| information_schema     |
| mysql                  |
| performance_schema     |
| sub_analytics | 👈 이게 보이면 성공!
| sys                    |
+------------------------+
```

테이블 확인:
```sql
USE sub_analytics;
SHOW TABLES;
```

**17개 테이블**이 생성되어 있어야 합니다:
```
+------------------------------------------+
| Tables_in_sub_analytics         |
+------------------------------------------+
| click_cancel_plan_button                 |
| click_content_page_more_review_button    |
| click_content_page_start_content_button  |
| click_lesson_page_related_question_box   |
| complete_lesson                          |
| complete_signup                          |
| complete_subscription                    |
| end_content                              |
| enter_content_page                       |
| enter_lesson_page                        |
| enter_main_page                          |
| enter_payment_page                       |
| enter_signup_page                        |
| renew_subscription                       |
| resubscribe_subscription                 |
| start_content                            |
| start_free_trial                         |
+------------------------------------------+
17 rows in set (0.00 sec)
```

데이터가 제대로 들어갔는지 확인:
```sql
-- 주요 테이블 데이터 개수 확인
SELECT 'complete_signup' AS table_name, COUNT(*) AS row_count FROM complete_signup
UNION ALL
SELECT 'complete_subscription', COUNT(*) FROM complete_subscription
UNION ALL
SELECT 'enter_lesson_page', COUNT(*) FROM enter_lesson_page
UNION ALL
SELECT 'start_content', COUNT(*) FROM start_content;
```

예상 결과:
```
+------------------------+-----------+
| table_name             | row_count |
+------------------------+-----------+
| complete_signup        |    145133 | 👈 회원가입 데이터
| complete_subscription  |     14289 | 👈 구독 시작 데이터
| enter_lesson_page      |  21029707 | 👈 레슨 페이지 방문 (2천만 건!)
| start_content          |    124917 | 👈 콘텐츠 시작 데이터
+------------------------+-----------+
```

**🎉 위와 같은 결과가 나오면 데이터 적재 완료!**

MySQL 종료:
```sql
EXIT;
```

---

## 3. 데이터 확인하기

### MySQL Workbench에서 확인

**Step 1: 데이터베이스 선택**

좌측 Navigator에서:
```
Schemas
  └─ sub_analytics  👈 방금 만든 데이터베이스를 찾으세요
      └─ Tables (17개 테이블이 있어요!)
          ├─ click_cancel_plan_button
          ├─ complete_lesson
          ├─ complete_signup
          ├─ complete_subscription
          ├─ enter_lesson_page
          ├─ renew_subscription
          ├─ start_content
          └─ ... 외 10개 테이블
```

💡 **만약 보이지 않는다면?** 좌측 Navigator에서 🔄 새로고침 버튼을 클릭하세요!

**Step 2: 간단한 쿼리 실행**

새 SQL 탭 열기 (단축키: `Cmd+T` / `Ctrl+T`)

```sql
-- 1. 데이터베이스 선택
USE sub_analytics;

-- 2. 어떤 테이블들이 있는지 확인
SHOW TABLES;

-- 3. 각 테이블 데이터 개수 확인
SELECT 'complete_signup' AS table_name, COUNT(*) AS row_count FROM complete_signup
UNION ALL
SELECT 'complete_subscription', COUNT(*) FROM complete_subscription
UNION ALL
SELECT 'enter_lesson_page', COUNT(*) FROM enter_lesson_page
UNION ALL
SELECT 'start_content', COUNT(*) FROM start_content;

-- 4. 신규 가입 데이터 확인 (처음 10개)
SELECT * FROM complete_signup LIMIT 10;

-- 5. 구독 시작 데이터 확인
SELECT * FROM complete_subscription LIMIT 10;
```

번개 버튼 ⚡ 클릭하면 실행됩니다!

---

## 4. SQL 쿼리 실행하기

### 데이터베이스 구조

Import한 데이터베이스에는 **17개의 이벤트별 테이블**이 있습니다:

```sql
-- 주요 테이블 목록
SHOW TABLES;

/*
결과 예시:
- click_cancel_plan_button       (구독 취소 버튼 클릭)
- complete_lesson                 (레슨 완료)
- complete_signup                 (회원가입 완료)
- complete_subscription           (구독 시작)
- enter_lesson_page               (레슨 페이지 방문)
- renew_subscription              (구독 갱신)
- start_content                   (콘텐츠 시작)
... 등등
*/
```

### 기본 쿼리 예제

**1. 신규 가입자 수 확인**

```sql
USE sub_analytics;

-- 일별 신규 가입자 수
SELECT
    DATE(client_event_time) AS signup_date,
    COUNT(*) AS new_users
FROM complete_signup
GROUP BY DATE(client_event_time)
ORDER BY signup_date;
```

**2. 구독 시작 현황**

```sql
-- 월별 구독 시작 수
SELECT
    DATE_FORMAT(client_event_time, '%Y-%m') AS month,
    COUNT(*) AS subscriptions
FROM complete_subscription
GROUP BY month
ORDER BY month;
```

**3. 플랫폼별 사용자 분포**

```sql
-- 어떤 플랫폼을 많이 쓰는지
SELECT
    platform,
    COUNT(*) AS user_count
FROM complete_signup
GROUP BY platform
ORDER BY user_count DESC;
```

### 미리 준비된 SQL 쿼리 파일 사용하기

프로젝트의 `sql/` 폴더에 분석용 쿼리가 준비되어 있습니다:

```
sql/
├── 01_data_validation.sql       # 데이터 확인
├── 02_acquisition.sql           # 신규 가입자 분석
├── 03_activation.sql            # 첫 사용 분석
├── 04_retention.sql             # 재방문 분석
├── 05_revenue.sql               # 구독 및 매출 분석
└── 06_funnel_analysis.sql       # 전환율 분석
```

**사용 방법:**
1. MySQL Workbench에서 **File** → **Open SQL Script**
2. 원하는 `.sql` 파일 선택
3. 쿼리 실행 ⚡

---

## 5. 문제 해결

### 문제 1: "ERROR 1045: Access denied"

비밀번호가 틀렸거나 다른 비밀번호가 설정되어 있습니다!

**올바른 접속 방법 (Mac & Windows 동일):**
```bash
mysql -u root -p
# 비밀번호 입력: Codeit10!
```

---

**💡 상황별 해결 방법:**

#### **상황 A: 비밀번호를 설정하지 않았다면**

Mac Homebrew 설치 직후에는 비밀번호가 없을 수 있습니다:
```bash
# 1. 비밀번호 없이 접속 시도
mysql -u root

# 2. 비밀번호 설정
ALTER USER 'root'@'localhost' IDENTIFIED BY 'Codeit10!';
FLUSH PRIVILEGES;
EXIT;

# 3. 이제부터는 -p 옵션 사용
mysql -u root -p
# 비밀번호: Codeit10!
```

---

#### **상황 B: 다른 비밀번호가 이미 설정되어 있다면 (현재 상황!)**

MySQL을 이전에 설치했거나 다른 비밀번호를 설정했다면, **비밀번호를 리셋**해야 합니다.

**Mac 사용자 - 비밀번호 리셋 방법:**

```bash
# Step 1: MySQL 서비스 중지
brew services stop mysql

# Step 2: 안전 모드로 MySQL 시작 (인증 건너뛰기)
mysqld_safe --skip-grant-tables &

# Step 3: 새 터미널 창 열어서 비밀번호 없이 접속
mysql -u root

# Step 4: MySQL 프롬프트에서 비밀번호 변경
FLUSH PRIVILEGES;
ALTER USER 'root'@'localhost' IDENTIFIED BY 'Codeit10!';
EXIT;

# Step 5: 안전 모드 프로세스 종료
killall mysqld

# Step 6: 정상 모드로 MySQL 재시작
brew services start mysql

# Step 7: 새 비밀번호로 접속 확인
mysql -u root -p
# 비밀번호 입력: Codeit10!
```

**Windows 사용자 - 비밀번호 리셋 방법:**

```cmd
REM Step 1: 관리자 권한으로 명령 프롬프트 실행

REM Step 2: MySQL 서비스 중지
net stop MySQL80

REM Step 3: 안전 모드로 MySQL 시작
mysqld --skip-grant-tables

REM Step 4: 새 명령 프롬프트 창 열어서
mysql -u root

REM Step 5: MySQL 프롬프트에서 비밀번호 변경
FLUSH PRIVILEGES;
ALTER USER 'root'@'localhost' IDENTIFIED BY 'Codeit10!';
EXIT;

REM Step 6: mysqld 프로세스 종료 (작업 관리자에서 mysqld.exe 종료)

REM Step 7: 정상 모드로 MySQL 재시작
net start MySQL80

REM Step 8: 새 비밀번호로 접속 확인
mysql -u root -p
REM 비밀번호 입력: Codeit10!
```

---

#### **상황 C: 그래도 안 된다면**

**가장 빠른 방법: MySQL 완전 재설치**

**Mac:**
```bash
# 1. MySQL 완전 삭제
brew services stop mysql
brew uninstall mysql
brew cleanup
rm -rf /usr/local/var/mysql
rm -rf /usr/local/etc/my.cnf

# 2. 재설치
brew install mysql

# 3. MySQL 시작
brew services start mysql

# 4. 비밀번호 설정
mysql -u root
ALTER USER 'root'@'localhost' IDENTIFIED BY 'Codeit10!';
FLUSH PRIVILEGES;
EXIT;
```

**Windows:**
1. 제어판 → 프로그램 제거 → MySQL Server 8.0 제거
2. `C:\ProgramData\MySQL` 폴더 삭제
3. MySQL 재설치: https://dev.mysql.com/downloads/installer/
4. 설치 중 root 비밀번호를 `Codeit10!`로 설정

---

### 문제 2: "No such file or directory" 또는 파일을 찾을 수 없음

**원인:** 잘못된 위치에서 명령어를 실행했습니다!

**해결 방법:**

#### Step 1: 현재 위치 확인

**Mac:**
```bash
pwd
# 결과가 /Users/내이름/Documents/sub_analytics 가 아니면 잘못된 위치!
```

**Windows:**
```cmd
cd
REM 결과가 C:\Users\내이름\Documents\sub_analytics 가 아니면 잘못된 위치!
```

#### Step 2: 프로젝트 폴더로 이동

**Mac:**
```bash
cd ~/Documents/sub_analytics
```

**Windows:**
```cmd
cd C:\Users\내이름\Documents\sub_analytics
```

#### Step 3: datas 폴더 확인

**Mac:**
```bash
ls
# datas 폴더가 보여야 합니다!

ls datas/
# "주제 2. 구독서비스 프로덕트 데이터 분석" 폴더가 보여야 합니다!
```

**Windows:**
```cmd
dir
REM datas 폴더가 보여야 합니다!

dir datas\
REM "주제 2. 구독서비스 프로덕트 데이터 분석" 폴더가 보여야 합니다!
```

#### Step 4: 다시 데이터 적재 명령어 실행

**Mac:**
```bash
mysql -u root -p --default-character-set=utf8mb4 sub_analytics < "datas/주제 2. 구독서비스 프로덕트 데이터 분석/DAproject_middle1_topic2_dump.sql"
```

**Windows:**
```cmd
mysql -u root -p --default-character-set=utf8mb4 sub_analytics < "datas\주제 2. 구독서비스 프로덕트 데이터 분석\DAproject_middle1_topic2_dump.sql"
```

---

### 문제 3: "ERROR 1049: Unknown database"

데이터베이스를 먼저 생성했는지 확인하세요!

```sql
-- 어떤 데이터베이스가 있는지 확인
SHOW DATABASES;

-- 만약 sub_analytics가 없다면 생성
CREATE DATABASE sub_analytics CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

-- 데이터베이스 사용
USE sub_analytics;
```

---

### 문제 4: Import가 너무 느려요

SQL dump 파일이 7GB라서 시간이 좀 걸립니다 (5-10분 정도).

**빨리 끝내는 팁:**

- ☕ 커피 한 잔 타서 마시고 오세요
- 터미널에서 실행하면 진행 상황을 볼 수 있어요
- 백그라운드에서 다른 작업을 하면서 기다리세요

---

### 문제 5: 쿼리가 너무 느려요

대용량 데이터라서 **항상 LIMIT을 사용**하세요!

```sql
-- ❌ 느림: 전체 데이터 조회 (절대 하지 마세요!)
SELECT * FROM complete_signup;

-- ✅ 빠름: 일부만 조회
SELECT * FROM complete_signup LIMIT 100;

-- ✅ 빠름: 특정 기간만 조회
SELECT *
FROM complete_signup
WHERE DATE(client_event_time) >= '2024-01-01'
LIMIT 1000;
```

---

### 문제 6: "Character set 'utf8m4' is not a compiled character set"

**원인:** 문자셋 이름을 잘못 입력했습니다!

**해결:**
- ❌ 틀린 것: `utf8m4` (b가 빠짐)
- ✅ 올바른 것: `utf8mb4` (b가 있어야 함!)

```bash
# 올바른 명령어
mysql -u root -p --default-character-set=utf8mb4 sub_analytics < "파일경로.sql"
```

---

### 문제 7: MySQL이 실행되지 않아요

**Mac 사용자:**
```bash
# MySQL 상태 확인
brew services list

# stopped 상태라면 다시 시작
brew services start mysql
```

**Windows 사용자:**
1. 작업 관리자 열기 (`Ctrl+Shift+Esc`)
2. "서비스" 탭으로 이동
3. "MySQL80" 찾기
4. 우클릭 → "시작"

---

## 6. 다음 단계

데이터 적재가 완료되었다면:

### ✅ 데이터 이해하기
**[data_dictionary.md](data_dictionary.md)** - 각 테이블과 컬럼 설명

### ✅ 분석 시작하기
**[analysis_guide.md](analysis_guide.md)** - AARRR 분석 가이드

### ✅ SQL 쿼리 실행
**sql/** 폴더의 쿼리 파일들 실행해보기

---

## 참고: 데이터베이스 구조

Import 후 생성되는 테이블 목록:

| 테이블명 | 설명 | AARRR 단계 |
|---------|------|-----------|
| `complete_signup` | 회원가입 완료 | Acquisition |
| `enter_lesson_page` | 레슨 페이지 진입 | Activation |
| `start_content` | 콘텐츠 시작 | Activation |
| `complete_lesson` | 레슨 완료 | Retention |
| `complete_subscription` | 구독 시작 | Revenue |
| `renew_subscription` | 구독 갱신 | Revenue |
| `click_cancel_plan_button` | 구독 취소 클릭 | Revenue (Churn) |
| ... 외 10개 테이블 | 기타 이벤트들 | - |

**💡 팁:** 각 테이블은 **특정 이벤트 하나**만 담고 있습니다.
- 예: `complete_signup` 테이블 = 회원가입 완료 이벤트만
- AARRR 분석 시 **여러 테이블을 JOIN**해서 사용합니다!

---

## 자주 묻는 질문

**Q: Excel 파일(중급1_구독서비스 데이터 이벤트 명세서.xlsx)은 어떻게 해요?**

A: 그 파일은 **참고 문서**일 뿐입니다. 데이터베이스에 적재하지 않아도 됩니다.
각 이벤트가 무엇을 의미하는지 설명해주는 명세서예요.

**Q: 데이터베이스 이름을 바꾸고 싶어요**

A: 데이터베이스 생성할 때 원하는 이름으로 만들면 됩니다!
```sql
-- 예: 'my_analysis'라는 이름으로 만들고 싶다면
CREATE DATABASE my_analysis CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

-- 터미널에서 적재할 때도 그 이름 사용
mysql -u root --default-character-set=utf8mb4 my_analysis < "파일경로.sql"
```

하지만 가이드와 일치하게 `sub_analytics`를 사용하는 걸 추천합니다!

**Q: 테이블 구조를 보고 싶어요**

A: 이 명령어를 사용하세요:
```sql
-- 테이블 구조 확인
DESCRIBE complete_signup;

-- 또는
SHOW CREATE TABLE complete_signup;
```

---

**🔥 Shift+Enter에 마음을 불태워, 에러를 넘어 인사이트까지🚀**
