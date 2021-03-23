# vue 실행

Node.js, vue, visual studio code 설치 

  

명령어 

$ npm install -g @vue/cli  

 : vue cli 설치 

$ vue --version : 버전 확인 (버전이 3이상이여야 서버 실행 가능) 

$ vue create 프로젝트 이름 : 프로젝트 생성 

  

Package.json 파일에서 확인 가능 

$ npm run serve : 프로젝트 서버 실행 

$ npm run build : 프로젝트 빌드   

  

  

Git 연동 

git init 

root 하위에 .gitignore 파일 생성 

git remote add origin "https://github.com/bumsgy/ㅁㄴㅁㄴㅁㄴㅁㄴ.git" 

Git add . 

Git commit -m "message" 

Git push --set-upstream orgin master 
   

  

visualStudio 확장플러그인 (깔면 좋음!) 

vetur설치 vuejs 문법강조, 자동완성등 

Material Icon Theme 아이콘테마 

ESLint 문법검삭  

TSLint 문법검삭 

Live Server 5500번 으로 서버 띄움 

korean 한글 패치 

  

  

Bootstrap 설치 

Npm install bootstrap-vue bootstrap --save 

  

Main.js에 추가 

Import BootstrapVue from 'bootstrap-vue' 

Import 'bootstrap/dist/css/bootstrap.css' 

Import 'bootstrap-vue/dist/bootstrap-vue.css' 

Vue.us(BootstrapVue) 

  

Bootstrap css 참고 

https://bootstrap-vue.org/docs/components 

  

  

  

  

Src : components 안에 vue파일 위치 

Main.js -> App.vue -> components 내 vue 파일 

  

Main.js에서 App.vue를 import 

App.vue에서 

<template> 

  <div id="app"> 

    <div id="header"> 

      <main-header/> 

    </div> 

  </div> 

</template> 

  

<script> 

import Header from './components/Header.vue'; 

  

export default { 

  name: 'App', 

  components: { 

    'main-header' : Header   

  }, 

}; 

</script> 

  

Header.vue에서 

<template> 

    <div> 

        <b-nav tabs> 

            <b-nav-item active>직원목록</b-nav-item> 

            <b-nav-item>장비관리</b-nav-item> 

            <b-nav-item>관리자메뉴</b-nav-item> 

        </b-nav> 

    </div> 

</template> 

<script> 

  export default { 

    name: 'main-header', 

    data: () => ({ 

    }), 

  } 

</script> 

  

  

로그인 참고 페이지 

https://lovemewithoutall.github.io/it/vue-login-demo/ 

  

  

게시판만들기 

[Bootstrap Vue로 게시판 만들기] 6. css flex 속성 

  

d/ 
otstrap 
6. CSS - flex 
  

![vue6](https://user-images.githubusercontent.com/58843821/112083190-f0d35080-8bc9-11eb-8081-426e465267ad.png)

  

Vue proxy 연결하기 (백엔드와 프론트엔드 연결하기) 

프론트엔드 - localhost:8080 

백엔드 - localhost:8082    서로 다른 포트 사용 

Vue.config.js에 설정 

module.exports = {  

     devServer: { 

            proxy: {  

                 '/api': {  

                             target: 'http://localhost:8082' // 개발서버 , 

 changeOrigin : true 

  }  

             }  

      }  

} 

  

npm add axios로 설치 

  

프로젝트에 axios 추가 

npm install --save axios 

  

Main.js에 import axios from 'axios' 

Vue.prototype.$axios = axios; 작성 

  

Vue파일에 해당 메서드에 axios  작성 

<<기본>> -> 모든 전달값을 config 객체로 전달하는 특징 

getMember : function () { 

    axios({ 

       method: 'GET', 

       url: 'http://192.168.1.40:8083/emp/list',      //api 링크 

       params : {   //파라미터 값 넣어주기 

                } 

    }).then((response) => { 

       console.log(response); 

       this.datas = response.data;      //성공했을 때 

    }).catch((ex) => { 

       console.log("ERR!!!!!!!!!!!!!", ex);      //실패했을 때 

    }) 

} 

  

<<get>> 

etchContactOne : function() { 

    axios.get('/api/contacts/' + this.no) 

    .then((response) => { 

        console.warn(response); 

        this.result = response.data 

    }) 

} 

  

<<post>> 

addContact : function() { 

    axios.post('/api/contacts',  

        { name:this.name, tel:this.tel, address:this.address } 

    ).then(response => { 

        console.warn(response) 

        this.result = response.data 

        this.no = response.data.no 

    }).catch((ex) => { 

        console.warn("ERROR!!!!! : ",ex) 

    }) 

} 

  

<<put>> (update) 

updateContact : function() { 

    axios.put('/api/contacts/' + this.no,  

        { name:this.name, tel:this.tel, address:this.address } 

    ).then(response => { 

        console.warn(response) 

        this.name = ''; 

        this.tel = ''; 

        this.address = ''; 

        this.result = response.data 

    }).catch((ex) => { 

        console.warn("ERROR!!!!! : ",ex) 

    }) 

} 

  

<<delete>> 

deleteContact : function() { 

    axios.delete('/api/contacts/' + this.no) 

    .then(response => { 

        console.warn(response) 

        this.result = response.data 

    }).catch((ex) => { 

        console.warn("ERROR!!!!! : ",ex) 

    }) 

} 

  

  

회사 장비관리 프로젝트 

상단 css 공통 : Header.vue (App.vue에서 import 중) 

장비목록 : Board.vue 

-> 목록 클릭 했을 때 : ContentDetail.vue 

-> 추가버튼 & 수정버튼 : Create.vue 

회원관리목록 : Member.vue 

-> 목록 클릭 했을 때 : MemberDetail.vue 

-> 추가버튼 & 수정버튼 : MemberAdd.vue 

 

라우터이동은 router – index.js에서 관리 

 

  

 
