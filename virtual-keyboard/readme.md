## 1. *prettier*와 *eslint* 설정 과정에서의 오류.
```js
PS D:\Virtual-Keyboard> npm i -D eslint-config-prettier eslint-plugin-prettier
npm ERR! code ERESOLVE
npm ERR! ERESOLVE unable to resolve dependency tree
npm ERR! ERESOLVE unable to resolve dependency tree
npm ERR!
npm ERR! While resolving: virtual-keyboard@1.0.0
npm ERR! While resolving: virtual-keyboard@1.0.0
npm ERR! Found: prettier@2.5.1
npm ERR! node_modules/prettier
npm ERR!   dev prettier@"2.5.1" from the root project
npm ERR!   dev prettier@"2.5.1" from the root project
npm ERR!
npm ERR!
npm ERR! Could not resolve dependency:
npm ERR! peer prettier@">=3.0.0" from eslint-plugin-prettier@5.2.1
npm ERR! node_modules/eslint-plugin-prettier
npm ERR! node_modules/eslint-plugin-prettier
npm ERR!   dev eslint-plugin-prettier@"*" from the root project
npm ERR!
npm ERR! Fix the upstream dependency conflict, or retry
npm ERR! this command with --force or --legacy-peer-deps
npm ERR! to accept an incorrect (and potentially broken) dependency resolution.
npm ERR!
npm ERR!
npm ERR! For a full report see:
npm ERR! C:\Users\mkyeo\AppData\Local\npm-cache\_logs\2024-09-29T11_02_23_205Z-eresolve-report.txt

npm ERR! A complete log of this run can be found in:
npm ERR!     C:\Users\mkyeo\AppData\Local\npm-cache\_logs\2024-09-29T11_02_23_205Z-debug-0.log
```

### 오류 발생 이유
- Node.js 프로젝트에서 패키지 설치 시 의존성 충돌로 인해 발생하는 문제. 
- 특정 패키지 호환 안됨/ 버전 충돌
- 
### <해결 시도>

### 1. 강제 설치<br>
```
npm install --legacy-peer-deps
```
-> 해결 X
### 2. npm 캐시 삭제 후 재시도
#### 
```
npm cache clean --force
npm install
```
-> 해결 X

### < 결론 >

  ```
  오류 메시지를 다시 보면, 'Prettier' 패키지의 버전이 충돌하여 의존성 해결에 실패한 상황이었다.
  사용하려는 'Prettier 버전'은 2.5.1인데, 'eslint-plugin-prettier@5.2.1' 은 3.0.0이상의 버전을 사용하길 권장한다. 
  때문에, npm이 의존성 트리를 해결하지 못하고 있었다.
  ```


### *Prettier*를 최신버전으로 업데이트
#### 
```
npm install prettier@latest --save-dev 
npm install -D eslint-config-prettier eslint-plugin-prettier
```
-> 오류 해결!

- 긴 **ERR** 창에 당황해서 *prettier* 버전 문제인걸 나중에서야 발견한 것이 오류를 수정하는데 오래 걸린 원인.  


