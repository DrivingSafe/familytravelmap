# 배포 가이드

`index.html` 하나로 동작하는 정적 웹앱입니다. 서버·데이터베이스가 필요 없고, 아래 세 방법 중 편한 것을 고르면 됩니다.

## 0. 지금 바로 써보기 (설정 없음)

채팅에서 받은 미리보기 링크로 바로 폰에서 켤 수 있습니다. 다만 그 링크는 임시 미리보기라 **주소가 바뀔 수 있고 파일 다운로드가 막혀 있어요.** 가족이 계속 쓸 주소를 원한다면 아래 1번(넷리파이)이 제일 빠릅니다.

## 1. Netlify Drop — 가장 빠름 (계정 필요, CLI·터미널 불필요)

1. https://app.netlify.com/drop 접속 (Netlify 무료 계정으로 로그인)
2. 이 프로젝트 폴더(`my-korea-journey`) 전체를 브라우저 화면에 그대로 드래그 앤 드롭
3. 몇 초 뒤 `https://무작위이름.netlify.app` 주소가 생성됩니다 — 이 주소를 가족에게 공유하세요
4. (선택) Netlify의 "Site settings → Change site name"에서 주소를 원하는 이름으로 바꿀 수 있습니다

이후 파일을 수정하면, 같은 화면에서 폴더를 다시 드래그하면 갱신됩니다.

## 2. GitHub Pages — 무료, 안정적 (GitHub 계정 필요)

터미널에서 이 폴더 기준으로 실행하세요:

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/사용자명/저장소이름.git
git push -u origin main
```

그다음 GitHub 저장소 페이지에서:
1. **Settings → Pages**
2. **Source**를 "Deploy from a branch"로, **Branch**를 `main` / `/(root)`로 설정 후 저장
3. 1~2분 뒤 `https://사용자명.github.io/저장소이름/` 에서 접속 가능

> `git remote add`의 URL은 GitHub에서 새 저장소를 먼저 만든 뒤 그 저장소 페이지에 표시되는 주소를 그대로 복사해 쓰면 됩니다.

## 3. Vercel — GitHub 연동 시 자동 배포

1. GitHub Pages처럼 저장소를 만들고 push
2. https://vercel.com 에서 "Add New → Project"로 그 저장소를 선택 → Deploy
3. 이후 `git push`할 때마다 자동으로 재배포됩니다

## 배포 후 확인할 것

- **PWA 설치**: 모바일 브라우저로 접속 후 "홈 화면에 추가"를 하면 앱처럼 아이콘이 생기고 오프라인에서도 실행됩니다 (`sw.js`가 지도 데이터까지 캐싱합니다).
- **아이콘 교체**: `icon.svg`를 원하는 로고로 바꾸면 홈 화면 아이콘도 함께 바뀝니다.
- **캐시 갱신**: 배포 후 코드를 수정했는데 사용자 화면에 반영이 안 된다면, `sw.js` 맨 위의 `const CACHE = 'korea-journey-v1'` 값을 `v2`처럼 올려주세요. 오프라인 캐시를 강제로 새로고침합니다.
- **가족 공유**: 주소가 정해지면, 앱 안의 "🔗 가족과 공유"에서 만든 링크는 이 주소를 기준으로 생성됩니다. 주소를 옮기면(예: 미리보기 → 실제 도메인) 기존에 만든 공유 링크는 예전 주소를 가리키니, 이전한 뒤 새로 링크를 다시 만들어 공유해주세요.
