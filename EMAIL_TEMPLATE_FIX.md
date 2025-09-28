# 📧 이메일 템플릿 수정 가이드

## 🚨 문제 상황
현재 보낸 사람이 `pat5987@kaist.ac.kr`로 설정되어 있음
→ **해결**: 보낸 사람을 폼에서 입력한 이메일로 변경

## 🔧 해결 방법

### 1. EmailJS 대시보드 접속
1. https://dashboard.emailjs.com/admin/templates 접속
2. **Templates** 탭 클릭
3. `template_2kif2hd` 템플릿 클릭하여 편집

### 2. 템플릿 설정 수정

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

#### **중요한 설정:**
1. **From Name**: `{{from_name}}` (보낸 사람 이름)
2. **From Email**: `{{from_email}}` (고정 - 실제 발송 계정)
3. **Reply To**: `{{from_email}}` ⭐ **이 부분이 중요!**
4. **To Email**: `pat5987@kaist.ac.kr` (받는 사람)

### 3. Reply To 설정 방법
1. 템플릿 편집 화면에서 **Advanced Settings** 클릭
2. **Reply To** 필드에 `{{from_email}}` 입력
3. **Save** 클릭

### 4. 결과
- **보낸 사람**: `pat5987@kaist.ac.kr` (발송 계정)
- **Reply To**: `사용자가 입력한 이메일` (답장할 때 사용)
- **받는 사람**: `pat5987@kaist.ac.kr`

## 🎯 최종 동작
1. 사용자가 Contact 폼 작성
2. 이메일이 `pat5987@kaist.ac.kr`에서 발송
3. **답장할 때는 사용자가 입력한 이메일로 자동 설정됨**
4. 사용자는 자신의 이메일로 답장을 받을 수 있음

## ✅ 확인 방법
1. 템플릿 수정 후 저장
2. 웹사이트에서 테스트 이메일 발송
3. 받은 이메일에서 "Reply" 버튼 클릭 시 사용자 이메일로 설정되는지 확인

---

**참고**: EmailJS에서는 보낸 사람을 변경할 수 없고, 대신 Reply To를 설정하여 답장 주소를 지정합니다.
