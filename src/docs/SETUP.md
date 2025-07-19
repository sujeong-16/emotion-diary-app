* 개발 환경 세팅 방법
# 1. 초기설정
1. vite 폴더 생성 (폴더위치는 D:\projects\my-diary-app\ )
- npm create vite@latest my-diary-app -- --template react

- 설치중 npm 에러 뜨면
    Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
를 터미널에 입력한다.
- 일시적으로만 실행 정책을 완화시켜주는 명령어이다. VSCode나 터미널에서 나가면 풀린다.


2. Firebase SDK 설치 (터미널에서 실행)
npm install firebase


3. src/services/firebase.js 파일 만들기
import { initializeApp } from "firebase/app";
import { getAuth } from "firebase/auth";
import { getFirestore } from "firebase/firestore";
import { getStorage } from "firebase/storage";

// 여기에 Firebase 콘솔에서 받은 설정 복붙
const firebaseConfig = {
  apiKey: "복붙",
  authDomain: "복붙",
  projectId: "복붙",
  storageBucket: "복붙",
  messagingSenderId: "복붙",
  appId: "복붙"
};

const app = initializeApp(firebaseConfig);

export const auth = getAuth(app);
export const db = getFirestore(app);
export const storage = getStorage(app);


4. 기본구조 연결 확인
실행은  npm run dev > o + Enter
실행취소는  Ctrl + C


5. gitignore 설정


6. Github 연결
```bash
git init
git remote add origin https://github.com/sujeong-16/emotion-diary-app.git   # 원격 저장소에 연결

# call: git config --global --add safe.directory D:/projects/my-diary-app~ 라고 에러나면 밑에 있는 명령어 입력하기. Git에 이 디렉토리가 안전하다고 등록하는 명령어이다.
git config --global --add safe.directory D:/projects/my-diary-app
git remote add origin https://github.com/sujeong-16/emotion-diary-app.git
git remote -v   # 연결 확인

# 밑에 내용처럼 출력된다면 OK
origin  https://github.com/sujeong-16/emotion-diary-app.git (fetch)
origin  https://github.com/sujeong-16/emotion-diary-app.git (push)

# 브랜치 설정하고 푸시하기
git branch -M main              # 브랜치 이름을 main으로 변경
git add .                       # 모든 파일을 스테이징
git commit -m "First commit"    # 커밋 생성
git push -u origin main         # 깃허브에 푸시


# 이후 프로젝트를 수정 후 깃허브에 반영할 때에는 3줄만 작성하면 된다.
git add .
git commit -m "수정 내용 간단 설명"
git push
```

※ git 완전 새로 시작하고 싶다면
1. .git 폴더 삭제 → 다시 init

```bash
rm -rf .git   # Windows면 rmdir /s /q .git
git init
git remote add origin https://github.com/sujeong-16/emotion-diary-app.git
git branch -M main
git add .
git commit -m "Initial commit with clean setup"
git push -f origin main
```