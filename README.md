# springBackend
jwt token과 redis를 이용한 스프링, 리액트, aws를 사용한 메모 프로젝트 입니다.<br>
backend : spring datajpa, jpa, lombok, spring security, jwt token<br>
frontend : react <br>
server : ec2, rds<br>
sql : mysql, h2
route 53 사용(Spring boot 책 참고)
application load balancer, auto scaling에 redis 넣어보기
<hr>

서버 주소들<br>
aws backend elastic ip : http://13.124.30.40:8080<br>
aws frontend elastic ip : http://13.124.30.40:3000<br>
<hr>

MYSQL RDS 설정 방법<br>
https://velog.io/@dohaeng0/AWS%EC%97%90-Spring-Boot-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%EB%B0%B0%ED%8F%AC-1-RDS-MySQL-%EC%84%B8%ED%8C%85<br>
<br>
백엔드 ec2 무중단 구성 (https://suyeoniii.tistory.com/52)<br>
java open jdk 11 설치<br>
ec2-user - https://www.geeksforgeeks.org/how-to-install-java-jdk11-on-aws-ec2/<br>
ubuntu - https://velog.io/@skyepodium/ubuntu-open-JDK-11-%EC%84%A4%EC%B9%98<br>
chmod +x gradlew <br>
./gradlew clean build<br>
nohup java -jar build/libs/demo-0.0.1.jar & > /dev/null<br>
<br>
프론트 무중단 구성 ( https://velog.io/@pp2lycee/pm2%EC%99%80-serve%EB%A1%9C-%EB%AC%B4%EC%A4%91%EB%8B%A8-%EC%84%9C%EB%B9%84%EC%8A%A4%ED%95%98%EA%B8%B0)<br>
nvm 설치 방법 : https://stackoverflow.com/questions/16904658/node-version-manager-install-nvm-command-not-found <br>
touch ~/.bash_profile<br>
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.1/install.sh | bash<br>
source ~/.nvm/nvm.sh<br>
nvm install 16.16.0<br>
nvm use 16.16.0<br>
(npm install --location=global serve)<br>
(npm install -g )<br>
npm install<br>
npm run build<br>
sudo npm install -g pm2@latest<br>
pm2 serve build 3000 --spa<br>
npm watch 설정: https://stackoverflow.com/questions/42772860/how-to-make-create-react-app-auto-build<br>

npm i --save-dev npm-watch<br>
<code>
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test --env=jsdom",
    "eject": "react-scripts eject",
    "watch": "npm-watch"
  },
  "watch": {
    "build": "src/"
  }
</code>
<br>
nginx 설정 (https://tobegood.tistory.com/entry/Nginx%EB%A1%9C-React%EB%A5%BC-%EB%B0%B0%ED%8F%AC%ED%95%98%EA%B8%B0-%EC%9A%B0%EB%B6%84%ED%88%AC-%ED%99%98%EA%B2%BD)<br>

<hr>


백엔드 <br>
전체 URL<br>
GET / : http://app.memoproject1.com:8080/ (헬스체크 용도)<br>
회원가입 POST auth/signup : http://app.memoproject1.com:8080/auth/signup<br>
로그인(jwt token 사용) POST auth/signin : http://app.memoproject1.com:8080/auth/signin <br>
메모 저장 <br>
메모 삭제 <br>
메모 가져오기 <br>
메모 변경하기 <br>

프론트엔드<br>
전체 URL<br>
로그인 GET /login    : http://app.memoproject1.com:3000/login<br>
회원가입 GET /signup : http://app.memoproject1.com:3000/signup<br>
메모페이지 GET /     : http://app.memoproject1.com:3000/ (유저 로그인 안되어 있는 경우에는 회원로그인 안됨)<br>

<hr>
<br>
<br>
백엔드 헬스체크 URL <br>
healthCheckPage : http://app.memoproject1.com:8080/ <br>

![image](https://github.com/sunggun1/springBackend/assets/17981550/503cd878-c24a-4475-b357-72c59f181705)

<br>
<br>

유저 로그인<br>

![image](https://github.com/sunggun1/springBackend/assets/17981550/8a5d5517-c9e1-48a5-831f-0b866569c82d) <br>

계정 생성<br>

![image](https://github.com/sunggun1/springBackend/assets/17981550/2a9e068a-245e-4c82-be3f-91d540dc1735) <br>

jwt token 사용 후 로그인한 사용자의 메모 페이지<br>
![image](https://github.com/sunggun1/springBackend/assets/17981550/f512f4c9-1bd1-40c1-9814-44bb42de71d8) <br>

메모 작성<br>
![image](https://github.com/sunggun1/reactFront/assets/17981550/5d75cdc6-f43e-455d-8dc7-8175aa2a1e37) <br>














