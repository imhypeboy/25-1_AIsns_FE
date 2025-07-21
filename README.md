# 📱 Date App - 소개팅 애플리케이션

**Date App**은 소개팅을 위한 사용자 연결 애플리케이션입니다. Firebase와 Spring Boot를 활용하여 회원가입부터 매칭 서비스까지 다양한 기능을 제공합니다.
성격키워드, mbti, 선호하는 사람(키워드)를 입력받아 AI자기소개글 자동 생성 기능을 제공합니다.
CI/CD 파이프라인을 사용하여 자동화된 코드 검증, 빌드, 배포가 이루어집니다.

---

## 🎯 주요 기능

### 1. **사용자 관리**
- **회원가입 및 로그인**
  - Firebase 인증 사용 (이메일, 비밀번호 기반).
  - JWT 기반 인증/인가 처리.
- **비밀번호 재설정**
  - 이메일을 통한 비밀번호 초기화 메일 발송.
- **회원 탈퇴**
  - Firebase Authentication 계정 삭제 및 Firebase Realtime Database 데이터 완전 삭제.

### 2. **프로필 관리**
- **프로필 조회**
  - 사용자 정보 (이름, 성별, 생년월일 등)와 MBTI, 태그, 자기소개 등을 표시.
- **프로필 수정**
  - 태그 및 선호 태그(최대 5개) 설정 가능.
  - 자기소개 작성 기능 제공(AI 자기소개글 생성 기능).
- **데이터 유효성 검증**
  - 필드별 제한사항 (최대 길이, 태그 개수 등) 검증 처리.

### 3. **매칭 서비스**
- **추천 엔진 기반 매칭**
  - 유사한 태그 및 MBTI를 기반으로 매칭 점수 계산.
  - 공통 관심사가 많은 사용자 추천.
- **추천 리스트 제공**
  - 추천된 사용자 목록을 매칭 점수 순으로 정렬 후 출력.

### 4. **보안 및 예외 처리**
- **JWT 기반 보안**
  - Spring Security를 바탕으로 필터 구현.
  - 모든 API 요청은 JWT 토큰을 통해 인증 처리.
- **글로벌 예외 처리**
  - 통일된 에러 메시지 출력 및 HTTP 상태 관리.
 
### 5. **CI/CD 파이프라인** ⚙️🚀
- GitHub Actions를 사용한 자동화된 빌드 및 배포.

---

## 🕹️ 주요 화면 및 흐름
<img width="616" height="1370" alt="image" src="https://github.com/user-attachments/assets/4b8a37f5-612a-45cc-8938-e09d8598ff36" />

<img width="604" height="1361" alt="image" src="https://github.com/user-attachments/assets/da1f40a8-b367-4169-bf44-5e070bc200d7" />
<img width="619" height="1368" alt="image" src="https://github.com/user-attachments/assets/a29a0d41-dcad-4f82-9cd2-ae62322698ce" />
<img width="603" height="1368" alt="image" src="https://github.com/user-attachments/assets/6a05729f-e5a2-4b25-a7e8-8c7727d03649" />
<img width="607" height="1366" alt="image" src="https://github.com/user-attachments/assets/604fec15-c14c-438c-b064-f92a879eb9ac" />
<img width="616" height="1370" alt="image" src="https://github.com/user-attachments/assets/27063e37-af75-4d20-905e-f4e3330238f2" />

### 🚪 **1. 로그인 / 회원가입**
- `login.html`
  - Firebase 인증을 통한 로그인.
  - 이메일 인증 미완료 시 접근 제한.
- `register.html`
  - 사용자 이메일, 비밀번호를 기반으로 회원가입.
  - 비밀번호 복잡성 유효성 검사.

### 🏠 **2. 홈 페이지**
- `home.html`
  - 간단한 소개 화면과 주요 기능 (프로필 조회, 매칭 추천)으로 이동하는 버튼 제공.
  
### 👤 **3. 프로필 페이지**
- `profile.html`
  - 사용자 개인 정보 조회 가능.
  - 프로필 수정 버튼을 통해 수정 페이지로 이동.
- `profileEdit.html`
  - 태그/선호 키워드 관리, MBTI 입력 등 프로필 수정 기능 제공.
  - 입력값 검증 및 Firebase 연동 저장 처리.

### 💌 **4. 매칭 추천 페이지**
- `match.html`
  - 추천된 사용자 리스트.
  - 매칭 점수, 공통 태그 표시.

---

## 🛠️ 프로젝트 기술 스택

### Backend
- **Spring Boot**
  - Spring Data JPA 및 Spring Security 사용.
  - Firebase와 연동을 위한 커스텀 서비스 및 필터 구현.
- **Firebase**
  - Firebase Authentication (이메일/비밀번호 인증).
  - Firebase Realtime Database (데이터 저장).
- **JWT**를 활용한 사용자 인증.

### Frontend
- **HTML + Thymeleaf**
  - 서버 사이드 렌더링(SSR).
  - 간단한 스타일 적용 및 자바스크립트를 통한 동적 기능 제공.
- **JavaScript**
  - Firebase SDK를 이용한 인증 흐름 관리.
  - AJAX를 활용한 비동기 API 통신.

### CI/CD 관련 도구
| 도구                   | 설명                                         |
|----------------------|--------------------------------------------|
| **GitHub Actions**   | 코드 변경에 따른 이벤트 트리거 및 모든 워크플로우 관리.          |
| **Gradle**           | 빌드 및 의존성 관리 도구로 프로젝트의 생명주기 제어.             |

---

## 📤 주요 Controller 및 Service

### 1. **Controller**
| 파일명               | 설명                                   |
|--------------------|--------------------------------------|
| `AuthController`   | 회원가입/로그인/로그아웃 관련 API 처리.            |
| `HomeController`   | 홈 화면(`/home`) 요청 처리.                |
| `MatchController`  | 매칭 추천 리스트 API 제공.                    |
| `ProfileController`| 사용자 프로필 조회/수정 페이지 및 API 처리.         |
| `FaviconController`| favicon 관련 리퀘스트 무시 처리.              |

### 2. **Service**
| 파일명                     | 설명                                       |
|--------------------------|------------------------------------------|
| `FirebaseAuthService`    | Firebase Auth와 통신하며 사용자 인증 및 데이터 관리. |
| `JwtUtil`                | JWT 토큰 생성 및 검증 처리.                    |
| `MatchService`           | 추천 매칭 목록 계산 및 반환 서비스.                |
| `MatchScoringService`    | 사용자 간 매칭 점수 계산.                        |

### 3. **Exception Handling**
| 파일명                   | 설명                             |
|------------------------|--------------------------------|
| `GlobalExceptionHandler` | 모든 예외를 통합 처리하여 일관된 에러 응답 제공. |

---

## 🔑 보안 설정

- **JWT 인증 필터**
  - `JwtAuthenticationFilter` 구현.
  - 사용자 요청의 `Authorization` 헤더에서 JWT 토큰을 읽고 인증 처리.
  
- **Firebase 인증 필터**
  - `FirebaseAuthenticationFilter`
  - Firebase 세션을 확인하여 사용자 인증 상태를 관리.

- **Spring Security 설정**
  - `SecurityConfig`에서 URL 접근 제어 및 요청 필터 설정.

---

## 📂 디렉토리 구조

```plaintext
📁 src
 ├── 📂 main
 │    ├── 📂 java/com/example/date_app
 │    │    ├── 📂 controller   # Controller 파일들
 │    │    ├── 📂 dto          # Data Transfer Object 정의
 │    │    ├── 📂 service      # 서비스 계층 구현
 │    │    ├── 📂 util         # 유틸리티 클래스
 │    │    ├── 📂 config       # Spring Security, Firebase 설정
 │    │    ├── 📂 security     # 보안 필터들 (JWT, Firebase)
 │    └── 📂 resources
 │         ├── 📂 templates   # Thymeleaf HTML 파일
 │         ├── 📂 static      # 정적 리소스 (이미지, CSS, JS)
 │         └── 📜 application.properties
```

---

## 🚀 CI/CD 파이프라인

### ⚙️ CI/CD 구성
이 프로젝트는 GitHub Actions를 기반으로 다음 프로세스를 포함한 CI/CD 파이프라인을 구현하고 있습니다.

1. **Git 이벤트 트리거**
   - `master` 브랜치에 `push` 또는 `pull_request` 발생 시 자동 실행.

2. **빌드 및 테스트**
   - Gradle을 이용한 프로젝트 빌드 및 의존성 관리.
   - `./gradlew clean build` 명령어로 애플리케이션을 빌드.

3. **Firebase 설정**
   - Firebase 서비스 계정 키(`firebase-service-account.json`)를 GitHub Secret에 인코딩된 형태로 저장.
   - CI 실행 시 JSON 파일을 복원하여 Firebase와 통신 가능하도록 설정.

4. **배포**
   - Gradle 빌드를 통해 생성된 `.jar` 파일을 원격 서버로 전송.
   - 기존 애플리케이션을 종료하고 새 애플리케이션을 백그라운드에서 시작.
   - 서버 로그를 통해 배포 상태를 확인.

5. **환경변수 설정**
   - GitHub Secret에서 환경변수를 추출하여 서버 환경에 자동 주입.
 
---

## 🚀 실행 방법

1. **코드 변경**: 개발자가 `master` 브랜치로 푸시하거나 Pull Request 생성.
2. **CI 실행**: 
   - GitHub Actions가 빌드 및 배포를 트리거.
   - Gradle 빌드 이후 결과물 `.jar` 파일을 생성.
3. **배포 및 재시작**: Remote 서버에 최신 버전 `.jar` 파일 업로드 및 애플리케이션 재시작.
4. **상태 확인**: 서버 로그(`/home/ubuntu/app/app.log`)로 최신 상태 확인 가능.

   - 브라우저에서 [http://210.109.54.109:8080](http://210.109.54.109:8080) 접속.
---

## ✨ 미리보기

### 홈 화면
![홈 화면](https://via.placeholder.com/800x400?text=홈+화면+미리보기)

### 매칭 추천 화면
![매칭 추천](https://via.placeholder.com/800x400?text=매칭+추천+화면)

---

## 🛡️ 라이선스
이 프로젝트는 **MIT License** 하에 배포됩니다.
