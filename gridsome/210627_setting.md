# Gridsome 이용해 블로그 기본 세팅하기

## Gridsome 설치~
```shell
npm install --global @gridsome/cli
```

## [Gridsome Blog Starter](https://github.com/gridsome/gridsome-starter-blog)을 이용한 세팅
### 1. Gridsome Blog Starter 생성
```shell
gridsome create my-blog https://github.com/gridsome/gridsome-starter-blog.git
cd my-blog
gridsome develop
```
### 2. github 리파지토리 연결

## gh-pages 이용해 Github Pages에 프로젝트 연결
### 1. gh-pages 설치
```shell
npm install gh-pages 
```

### 2. url 연결
`gridsome.config.js` 파일에 아래와 같이 추가
```json
// https://my-name.github.io/my-blog/ 에 연결됨
siteUrl: 'https://my-name.github.io',
pathPrefix: '/my-blog'
```

### 3. deploy 명령어 추가
`package.json`에 아래 명령어 추가 (scripts 항목에)
```json
"deploy": "gridsome build && gh-pages -d dist"
```

### 4. deploy 실행
아래 명령어를 터미널에서 실행하면
```shell
npm run deploy
```
dist 폴더가 생성되고, 빌드 결과물은 자동으로 gh-pages에 푸쉬되어 Github Pages에 연결된다.

---
#### 참고 사이트
- https://perade.github.io/blog/make-blog-with-gridsome-2nd/ : 아주 정리가 잘 되어있는 사이트. 감사합니다!
- [Gridsome 공식 문서](https://gridsome.org/docs/)