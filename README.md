## Next JS란?
: **React를 위해 만든 프레임워크**로, React에 없는 아래의 기능들을 제공해 준다.
1. 서버 사이드 렌더링 (SSR)
2. 정적 사이트 생성 (SSG)
3. 증분 정적 재생성 (ISR)

> [!TIP]
> React는 웹 프레임워크, 자바스크립트 라이브러리로 개발을 도와주는 도구이다.

<br/>

### 1. 서버 사이드 렌더링 (SSR)
모든 페이지에 대한 HTML이 서버 측에서 렌더링하여 생성한다.
<br/>
이는 검색 엔진에서 해당 페이지를 더 잘 인식하고 색인화하는 데 도움이 된다. (= 검색 엔진 최적화, **SEO**)
> SEO 영역에서의 색인화란? Google과 같은 검색 엔진이 웹 페이지 및 기타 온라인 콘텐츠를 데이터베이스에 저장하고 구성하는 과정이다.
> <br/>
> [서버 사이드 렌더링](https://patterns-dev-kr.github.io/rendering-patterns/server-side-rendering/)

<br/>

### 2. 정적 사이트 생성 (SSG)
정적 사이트란, 저장된 파일(HTML, JS, 이미지 등)을 그대로 보는 것을 말한다.
<br/>
따라서, 빌드 시점에 렌더링을 하기 때문에 매우 빠르게 로드될 수 있고, 모든 사용자에게 동일한 내용을 보여준다.
<br/>
(웹사이트를 만드는 데에 최적화되어 있음)
<br/>

_* 동적 사이트 : 변수들에 의해 변경되어 보이는 것_

<br/>

#### * SSR, SSG의 차이
SSR : 매 요청마다 HTML을 생성하기 때문에 비교적 응답 속도가 느리고, 서버에 더 많은 부담이 간다.
<br/>
SSG : 매 요청마다 HTML을 재사용하기 때문에 SSR보다 SSG를 권장한다.

<br/>

### 3. 증분 정적 재생성 (ISR)
설정한 시간마다 페이지를 새로 렌더링 한다.
<br/>
설정 시간은 `revalidate: 초;`로 지정한다. <sup>예시 코드를 작성할 때 보여드리겠습니다.</sup>
<br/>
이는, 동적이지만 자주 변경되지 않는 사이트에 사용하는 것을 추천한다. (ex. 블로그)
> SSG는 데이터가 변경되면 다시 빌드를 해야하지만,
> <br/>
> ISR은 일정 시간마다 특정 페이지만 다시 빌드하여 페이지를 업데이트 한다.

<br/>

***

<br/>

## Next JS 설치/실행
1. Node.js 설치 ➡️ 설치 후 터미널에서 `node -v` 입력해 설치 확인
2. 터미널에 `npx create-next-app@latest` 입력
3. 아래와 같은 메세지들이 뜬다.
```
What is your project named? 프로젝트명
Would you like to use TypeScript? No / Yes
Would you like to use ESLint? No / Yes
Would you like to use Tailwind CSS? No / Yes
Would you like to use `src/` directory? No / Yes
Would you like to use App Router? (recommended) No / Yes
Would you like to customize the default import alias (@/*)? No / Yes
What import alias would you like configured? @/*
```
4. `cd 프로젝트명`으로 이동
5. `npm run dev`를 입력하여 프로젝트를 실행한다. (개발 서버)
6. `http://localhost:3000` 접속하면 프로젝트를 확인할 수 있다.

<br/>

***

<br/>

## Next JS 파일 구조
프로젝트 열면 아래와 같은 파일 구조로 생성이 된다.
<br/>
<br/>
<img width="240" alt="image" src="https://github.com/ParkMiram/ParkMiram/assets/125454927/8c67c573-6fde-4fda-8c2a-228bda8a2106">
<br/>
+ **src**: 프로젝트 생성 당시 `Would you like to use `src/` directory? No / Yes`에서 Yes를 선택하면 자동으로 생성해 준다. (만들지 않아도 @/로 접근 가능하다.)
+ **app**: 코드 짤 폴더
+ **page.js**: 메인 페이지
+ **layout.js**: 루트 레이아웃에 추가하는 모든 UI는 애플리케이션의 모든 페이지 에서 공유된다. (중복을 줄일 수 있음)
+ **public**: 이미지나 static 파일 보관하는 폴더
+ **api**: 서버 기능 만드는 폴더
<br/>

+ **next.config.mjs**: NextJS 설정 파일
+ **node_modules**: 설치한 라이브러리 보관용 폴더
+ **package.json**: 설치한 라이브러리 버전 기록하는 파일

<br/>

***

<br/>

> [!NOTE]
> 서버 쪽은 express와 거의 동일하기 때문에 프론트 위주로 함!
> 예..예시 코드를 작성하고 싶었으나... 성공하지 못함.. 그래서 공식홈페이지에서 코드를 따옴ㅎ

<br/>

## 'use client'
> 서버와 클라이언트 코드 사이의 경계를 선언하는 데 사용된다. (동적으로 렌더링 된다, 정적인 사이트에선 사용❌)
> 
> 필요한 경우에만 렌더링을 사용함으로써, 서버의 부담을 줄이고 전체 애플리케이션의 성능을 최적화할 수 있다.
>
> ```
> 'use client'
> ```

<br/>

**사용 예시**
1. 입력 폼 검증 : 사용자 입력이 특정 조건을 만족하는지 실시간으로 확인/피드백 제공
2. 사용자 위치 기반 서비스 : 현재 위치를 기반으로 정보 제공
3. 실시간 데이터 시각화 : (웹소켓 사용) 서버로부터 실시간으로 데이터를 받아 차트나 그래프를 동적으로 업데이트
4. 클라이언트 측 암호화 : 사용자의 브라우저에서 데이터를 암호화하고 복호화하는 작업을 수행
5. 게임 또는 애니메이션 : 사용자의 입력에 반응하여 실시간으로 변화하는 게임이나 애니메이션 구현

<br/>

**사용하지 않는 예시**
1. 블로그 포스트 목록 : 서버에서 미리 렌더링 된 블로그 포스트 목록을 사용자에게 제공하여 빠른 페이지 로드
2. 정적인 페이지 : 마케팅 랜딩 페이지, 제품 카탈로그, FAQ, 회사 정보 페이지

<br/>

***

<br/>

## 라우팅
> 네트워크에서 경로를 선택

![image](https://github.com/ParkMiram/ParkMiram/assets/125454927/ebd3bce0-fbb6-4534-984a-320abf2c59ec)
![image](https://github.com/ParkMiram/ParkMiram/assets/125454927/81768d0d-e69c-45e6-877d-628c908429ad)

<br/>

> [!IMPORTANT]
> 페이지 접근하기 위해선 폴더 안에 page.js 또는 route.js가 있어야 한다.

<br/>

**useRouter**
<br/>
: Next JS의 내장 훅 중 하나로, 라우팅을 관리하는 데 사용이 된다.
<br/>
현재 페이지의 URL, 경로, 쿼리 파라미터 등과 같은 정보에 쉽게 액세스할 수 있다.
```
import { useRouter } from 'next/navigation'

export default function Page() {
    const router = useRouter()

    return (
        <button type="button" onClick={() => router.push('/dashboard')}>
            대시보드
        </button>
    )
}
```
router.replace() 메서드를 사용하면 페이지를 교체하고 이전 페이지를 히스토리 스택에서 제거할 수 있다.

<br/>

***

<br/>

## Cookie
1. 쿠키 이름으로 이름과 값이 있는 개체를 반환
```
import { cookies } from 'next/headers'
 
export default function Page() {
  const cookieStore = cookies()
  const cookieName = cookieStore.get('name')
  return '...'
}
```
2. 모든 쿠키 목록 반환
```
import { cookies } from 'next/headers'
 
export default function Page() {
  const cookieStore = cookies()
  return cookieStore.getAll().map((cookie) => (
    <div key={cookie.name}>
      <p>Name: {cookie.name}</p>
      <p>Value: {cookie.value}</p>
    </div>
  ))
}
```
3. 쿠키 존재 여부 확인 (boolean)
```
import { cookies } from 'next/headers'
 
export default function Page() {
  const cookieStore = cookies()
  const hasCookie = cookieStore.has('name')
  return '...'
}
```
4. 쿠키 이름으로 삭제
```
'use server' // 서버 작업 표시
 
import { cookies } from 'next/headers'
 
async function delete(data) {
  cookies().delete('name')
}
```


<!--
### Hi there 👋
🔭 I’m currently working on Play Data
![mysql](https://img.shields.io/badge/mysql-4479A1.svg?&style=for-the-badge&logo=mysql&logoColor=white)

[![Solved.ac Profile](http://mazassumnida.wtf/api/generate_badge?boj=박미람)](https://solved.ac/박미람)

![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=ParkMiram&layout=Demo&theme=dark)
-->

<!--
**ParkMiram/ParkMiram** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
