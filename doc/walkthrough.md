# GitClip Cloud Usage Guide

GitHub Gist를 백엔드로 사용하는 **Zero-Install 클립보드 동기화 도구**입니다.
PC와 모바일 어디서나 브라우저만 있으면 안전하게 텍스트를 공유할 수 있습니다.

## ✨ 주요 기능 (V5.1 Update)

*   **🔒 End-to-End 암호화 (E2EE)**: 비밀번호를 설정하면 브라우저에서 암호화 후 업로드됩니다. (서버도 내용 모름)
*   **☁️ Global Sync History**: 모든 기기의 저장 기록이 공유됩니다. (누가 저장했는지, 몇 번 읽혔는지 확인 가능)
*   **🔓 자동 복호화 미리보기**: 암호화된 내용도 History 목록에서 자동으로 풀어서 보여줍니다.
*   **📄 페이지네이션**: 데이터가 많아지면 페이지를 나눠서 보여줍니다. (속도 저하 방지)
*   **📱 PWA 지원**: 홈 화면에 추가하여 앱처럼 쓸 수 있습니다.
*   **🛠️ Safe Re-encrypt**: 비밀번호 변경 시 기존 데이터를 안전하게 재암호화합니다.

## 1. 시작하기 (Setup)

### 1) GitHub Token & Gist 준비 (최초 1회)
1.  **Token 생성**: [GitHub Tokens](https://github.com/settings/tokens) -> `Generate new token (classic)` -> `gist` 체크 -> 토큰 복사.
2.  **Gist 생성**: [gist.github.com](https://gist.github.com) -> 아무 내용(`init`) 쓰고 `Create secret gist` -> URL 뒤의 **ID 복사**.

### 2) 앱 설정
1.  우측 상단 **⚙️(설정)** 아이콘 클릭.
2.  **GitHub Token**과 **Gist ID** 입력.
3.  **Device Name** 본인 기기 이름 입력 (예: `My iPhone`).
4.  **Encryption Password** (선택) 원하는 암호 입력.
    *   *주의: 이 암호를 잊어버리면 데이터를 복구할 수 없습니다.*

## 2. 사용 방법

*   **Load (⬇️)**: 클라우드에서 최신 내용을 가져옵니다.
    *   암호화된 내용은 자동으로 풀어서 보여줍니다.
*   **Save (⬆️)**: 입력창의 내용을 클라우드에 저장합니다.
    *   암호가 설정되어 있으면 자동으로 잠그고 올립니다.
*   **History**: 하단 목록에서 이전 기록을 볼 수 있습니다.
    *   클릭하면 해당 내용을 불러옵니다.
    *   `[Prev] [Next]` 버튼으로 이전 페이지를 볼 수 있습니다.

## 3. 검증 (Verification)

### PC Browser Verification (V5.1 fix)
`browser_subagent`를 통해 다음 기능이 정상 작동함을 검증했습니다:
1.  **Page Load**: 빈 화면 문제 해결됨.
2.  **UI Check**: Settings 모달 열기/닫기, History 섹션 표시 정상.
3.  **Visual Proof**:
    ![Verification Video](file:///C:/Users/SDS/.gemini/antigravity/brain/8d97428c-11f7-4d67-a031-6fed85c92175/verify_gitclip_ui_fix_1768539783488.webp)

---
**Tip**: 모바일에서는 브라우저 메뉴의 "홈 화면에 추가"를 누르면 앱처럼 실행됩니다.
