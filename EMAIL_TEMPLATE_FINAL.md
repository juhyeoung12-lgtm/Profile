# 📧 EmailJS 템플릿 최종 설정 가이드

## 🎯 목표
- **보낸 사람**: 사용자가 입력한 이메일 (동적)
- **받는 사람**: pat5987@kaist.ac.kr (고정)

## 🔧 EmailJS 템플릿 설정

### 1. EmailJS 대시보드 접속
1. https://dashboard.emailjs.com/admin/templates 접속
2. **Templates** 탭 클릭
3. `template_2kif2hd` 템플릿 편집

### 2. 템플릿 설정 (중요!)

#### **템플릿 필드 설정:**
```
From Name: {{from_name}}
From Email: {{from_email}}
Reply To: {{from_email}}
To Email: pat5987@kaist.ac.kr
```

#### **템플릿 내용:**
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
```

### 3. 사용 가능한 변수들

#### **JavaScript에서 전송하는 변수:**
```javascript
{
    title: subject,        // 제목 (subject와 동일)
    name: name,           // 사용자 이름
    subject: subject,     // 제목
    message: message,     // 메시지 내용
    from_name: name,      // 보낸 사람 이름
    from_email: email     // 보낸 사람 이메일
}
```

#### **HTML 폼 필드 매핑:**
- `{{from_name}}` = `<input id="name">` (사용자 이름)
- `{{from_email}}` = `<input id="email">` (사용자 이메일)
- `{{subject}}` = `<input id="subject">` (제목)
- `{{message}}` = `<textarea id="message">` (메시지)

## 🎯 최종 동작 방식

### **사용자 시나리오:**
1. 사용자가 Contact 폼에 입력:
   - Name: "하늘"
   - Email: "moonn3940@gmail.com"
   - Subject: "연구 문의"
   - Message: "안녕하세요..."

2. JavaScript에서 전송:
   ```javascript
   {
       title: "연구 문의",
       name: "하늘",
       subject: "연구 문의",
       message: "안녕하세요...",
       from_name: "하늘",
       from_email: "moonn3940@gmail.com"
   }
   ```

3. 이메일 발송 결과:
   - **보낸 사람**: "하늘 <moonn3940@gmail.com>"
   - **받는 사람**: "pat5987@kaist.ac.kr"
   - **제목**: "[웹사이트 문의] 연구 문의"

## ✅ 확인 방법
1. 템플릿 설정 후 저장
2. 웹사이트에서 테스트 이메일 발송
3. pat5987@kaist.ac.kr 계정에서 이메일 확인
4. 보낸 사람이 사용자가 입력한 이메일로 표시되는지 확인

## 🚨 중요 사항
- **From Email**: `{{from_email}}`로 설정하여 동적 보낸 사람 설정
- **Reply To**: `{{from_email}}`로 설정하여 답장 주소 지정
- **To Email**: `pat5987@kaist.ac.kr`로 고정

---

**참고**: 이 설정으로 각 사용자마다 다른 보낸 사람 이메일이 표시됩니다.
