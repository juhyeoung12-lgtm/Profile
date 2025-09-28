# 📧 이메일 전송 기능 설정 가이드

## EmailJS 설정 방법

### 1. EmailJS 계정 생성 및 설정

1. **EmailJS 웹사이트 방문**: https://www.emailjs.com/
2. **회원가입**: 무료 계정 생성
3. **대시보드 접속**: 로그인 후 대시보드로 이동

### 2. 이메일 서비스 연결

1. **Email Services** 탭 클릭
2. **Add New Service** 클릭
3. **Gmail** 또는 **Outlook** 선택 (권장)
4. **Connect Account** 클릭하여 이메일 계정 연결
5. **Service ID** 복사 (예: `service_abc123`)

### 3. 이메일 템플릿 생성

1. **Email Templates** 탭 클릭
2. **Create New Template** 클릭
3. **템플릿 설정**:

```html
제목: 웹사이트 문의 - {{subject}}

내용:
안녕하세요,

다음과 같은 문의가 접수되었습니다:

보낸 사람: {{from_name}}
이메일: {{from_email}}
제목: {{subject}}

메시지:
{{message}}

--
이 메시지는 웹사이트 Contact 폼을 통해 전송되었습니다.
```

4. **Template ID** 복사 (예: `template_xyz789`)

### 4. Public Key 확인

1. **Account** 탭 클릭
2. **Public Key** 복사 (예: `user_abc123def456`)

### 5. 코드 수정

`script.js` 파일에서 다음 부분을 수정하세요:

```javascript
// 1. Public Key 설정 (94번째 줄)
emailjs.init("YOUR_PUBLIC_KEY"); // 여기에 실제 Public Key 입력

// 2. Service ID 설정 (146번째 줄)
'YOUR_SERVICE_ID', // 여기에 실제 Service ID 입력

// 3. Template ID 설정 (147번째 줄)
'YOUR_TEMPLATE_ID', // 여기에 실제 Template ID 입력

// 4. 받을 이메일 주소 설정 (141번째 줄) - 이미 설정됨
to_email: 'pat5987@kaist.ac.kr' // KAIST 이메일 주소
```

### 6. 설정 예시

```javascript
// 예시 설정
emailjs.init("user_abc123def456");

const response = await emailjs.send(
    'service_abc123',
    'template_xyz789',
    templateParams
);
```

### 7. 이메일 템플릿 예시 (KAIST용)

```html
제목: [웹사이트 문의] {{subject}}

내용:
안녕하세요,

다음과 같은 문의가 접수되었습니다:

보낸 사람: {{from_name}}
이메일: {{from_email}}
제목: {{subject}}

메시지:
{{message}}

--
이 메시지는 개인 홈페이지 Contact 폼을 통해 전송되었습니다.
수신자: pat5987@kaist.ac.kr
```

## 🔧 추가 설정 옵션

### 이메일 전송 제한 설정
- EmailJS 무료 계정: 월 200통 제한
- 유료 계정: 더 많은 이메일 전송 가능

### 스팸 방지 설정
1. **Rate Limiting** 활성화
2. **reCAPTCHA** 추가 (선택사항)
3. **도메인 제한** 설정

### 이메일 알림 설정
1. **Auto Reply** 템플릿 생성
2. **받는 사람에게 자동 응답** 설정

## 🚀 테스트 방법

1. 웹사이트에서 Contact 폼 작성
2. **Send Message** 버튼 클릭
3. 설정한 이메일 주소로 메시지 도착 확인
4. 브라우저 콘솔에서 에러 메시지 확인

## ❗ 문제 해결

### 이메일이 전송되지 않는 경우
1. **Public Key**, **Service ID**, **Template ID** 확인
2. **이메일 서비스 연결 상태** 확인
3. **브라우저 콘솔**에서 에러 메시지 확인
4. **EmailJS 대시보드**에서 전송 로그 확인

### 자주 발생하는 오류
- `Invalid Public Key`: Public Key가 잘못됨
- `Service not found`: Service ID가 잘못됨
- `Template not found`: Template ID가 잘못됨

## 📞 지원

EmailJS 관련 문제가 있을 경우:
- EmailJS 공식 문서: https://www.emailjs.com/docs/
- EmailJS 지원팀: support@emailjs.com

---

**참고**: 이 설정을 완료하면 웹사이트 방문자가 Contact 폼을 통해 실제 이메일을 보낼 수 있습니다.
