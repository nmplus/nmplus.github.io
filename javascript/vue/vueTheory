# Vue 이론

Vue란 ? 

MVVM 패턴의 ViewModel 레이어에 해당하는 화면단 라이브러리 
 -> MVVM : 화면 앞단의 화면 동 관련 로직과 뒷단의 DB 데이터 처리 및 서버 로직을 분리하고, 뒷단에서 넘어온 데이터를 Model에 담아 View로 넘겨주는 중간 지점 
 
 ![vue1](https://user-images.githubusercontent.com/58843821/112082772-40fde300-8bc9-11eb-97fc-45e09c7dc45a.png)
 
    - 데이터 바인딩과 화면 단위를 컴포넌트 형태로 제공하며, 관련 API를 지원하는데에 궁극적인 목적이 있음 

    - gular에서 지원하는 양방향 데이터 바인딩을 동일하게 제공 

    - 하지만 컴포넌트 간 통신의 기본 골격은 React의 단방향 데이터 흐름(부모->자식)을 사용 

    - 다른 프런트엔드 프레임워크(Angular, React)와 비교했을 때 상대적으로 가볍고 빠름 

    - 문법이 단순하고 간결하여 초기 습 비용이 낮고 누구나 쉽게 접근 가능 
    
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script> 

<script src="https://cdn.jsdelivr.net/npm/vue@2.6.0"></script> 

 

------------------------------------------------------------------------------------------------------ 

<div id="app">  

    {{ message }} 

</div> 

 

var app = new Vue({  

  el: '#app',  

  data: {  

      message: '안녕하세요 Vue!'  

  }  

}) 

  

-> 안녕하세요 Vue! 

----------------------------------------------------------------------------------------------------- 

 

 

-----------------------------------------------------------------------------------------------------  

<div id="app-2"> 

    <span v-bind:title="message">  

        내 위에 잠시 마우스를 올리면 동적으로 바인딩 된 title을 볼 수 있습니다!  

    </span>  

</div> 

  

var app2 = new Vue({  

    el: '#app-2',  

    data: {  

         message: '이 페이지는 ' + new Date() + ' 에 로드 되었습니다' }  

}) 

  

-> app2.message = '새로운 메시지'라고 입력하면 message 내용이 업데이트 되었음을 확인 가능 

----------------------------------------------------------------------------------------------------- 

  

 

----------------------------------------------------------------------------------------------------- 

<div id="app-3"> 

     <p v-if="seen">이제 나를 볼 수 있어요</p>  

</div> 

  

var app3 = new Vue({  

    el: '#app-3',  

    data: {  

         seen: true  

    }  

}) 

  

-> false로 바꾸면 메세지가 보이지 않음 

----------------------------------------------------------------------------------------------------- 

 

 

----------------------------------------------------------------------------------------------------- 

<div id="app-4">  

    <ol>  

        <li v-for="todo in todos">  

            {{ todo.text }}  

        </li>  

    </ol>  

</div> 

  

var app4 = new Vue({  

    el: '#app-4',  

    data: {  

        todos: [  

            { text: 'JavaScript 배우기' },  

            { text: 'Vue 배우기' },  

            { text: '무언가 멋진 것을 만들기' }  

        ]  

    }  

}) 

  

-> 

JavaScript 배우기 

Vue 배우기 

무언가 멋진 것을 만들기 

  

-> app4.todos.push({ text: 'New item' }) 을 입력하면 4.New item이 동적으로 추가 됨 

 ----------------------------------------------------------------------------------------------------- 

 

----------------------------------------------------------------------------------------------------- 

<div id="app-5">  

    <p>{{ message }}</p>  

    <button v-on:click="reverseMessage">메시지 뒤집기</button>  

</div> 

  

  

var app5 = new Vue({  

    el: '#app-5',  

    data: {  

        message: '안녕하세요! Vue.js!'  

    },  

    methods: {  

        reverseMessage: function () {  

            this.message = this.message.split('').reverse().join('')  

        }  

    }  

}) 

  

-> 메시지 뒤집기 버튼 클릭 시 !sj.euV !요세하녕안 

 ----------------------------------------------------------------------------------------------------- 

 

----------------------------------------------------------------------------------------------------- 

<div id="app-6">  

    <p>{{ message }}</p>  

    <input v-model="message">  

</div> 

  

var app6 = new Vue({  

    el: '#app-6',  

    data: {  

        message: '안녕하세요 Vue!'  

    }  

}) 

  

->   
![vue2](https://user-images.githubusercontent.com/58843821/112082771-40654c80-8bc9-11eb-8971-0514db7c5210.png)

----------------------------------------------------------------------------------------------------- 

 

 

컴포넌트 

// todo-item 이름을 가진 컴포넌트를 정의합니다  

Vue.component( 'todo-item', {  

    template: '<li>할일 항목 하나입니다.</li>' 

 })  

var app = new Vue(...) 

  

<ol>  

    <!-- todo-item 컴포넌트의 인스턴스 만들기 -->  

    <todo-item></todo-item>  

</ol> 

  

Vue.component( 'todo-item', {  

// 이제 todo-item 컴포넌트는 "prop" 이라고 하는  

// 사용자 정의 속성 같은 것을 입력받을 수 있습니다.  

// 이 prop은 todo라는 이름으로 정의했습니다.  

    props: ['todo'],  

    template: '<li>{{ todo.text }}</li>'  

}) 

  

<div id="app-7">  

    <ol>  

    <!-- 이제 각 todo-item 에 todo 객체를 제공합니다. 화면에 나오므로, 각 항목의 컨텐츠는 동적으로 바뀔 수 있습니다. 또한 각 구성 요소에 "키"를 제공해야합니다 (나중에 설명 됨). -->  

        <todo-item v-for="item in groceryList" v-bind:todo="item" v-bind:key="item.id" ></todo-item>  

    </ol>  

</div> 

  

Vue.component( 'todo-item', {  

    props: ['todo'],  

    template: '<li>{{ todo.text }}</li>'  

})  

  

var app7 = new Vue({ 

    el: '#app-7',  

    data: {  

        groceryList: [  

            { id: 0, text: 'Vegetables' },  

            { id: 1, text: 'Cheese' },  

            { id: 2, text: 'Whatever else humans are supposed to eat' }  

        ]  

    }  

}) 

  

  

Vue 인스턴스 

모든 Vue 앱은 Vue 함수로 새 Vue 인스턴스를 만드는 것부터 시작합니다. 

  

var vm = new Vue({  

    // 옵션  

}) 

  

각 Vue 인스턴스는 data 객체에 있는 모든 속성을 프록시 처리함 

  

// 데이터 객체  

var data = { a: 1 }  

  

// Vue인스턴스에 데이터 객체를 추가합니다.  

var vm = new Vue({  

    data: data  

})  

  

// 같은 객체를 참조합니다!  

vm.a === data.a // => true  

  

// 속성 설정은 원본 데이터에도 영향을 미칩니다.  

vm.a = 2  

data.a // => 2  

  

// ... 당연하게도  

data.a = 3  

vm.a // => 3 

 

 

Vue 라우터 

Vue와 Vue 라우터를 이용해 싱글 페이지 앱을 만드는 것은 매우 쉽습니다. Vue.js를 사용한다면 이미 컴포넌트로 앱을 구성하고 있을 것입니다. Vue 라우터를 함께 사용할 때 추가로 해야하는 것은 라우트에 컴포넌트를 매핑한 후, 어떤 주소에서 렌더링할 지 알려주는 것 뿐입니다. 

 
![vue3](https://user-images.githubusercontent.com/58843821/112082770-3fccb600-8bc9-11eb-83bf-4aab650b84bc.png)

![vue4](https://user-images.githubusercontent.com/58843821/112082768-3f341f80-8bc9-11eb-8277-94b2d56cb6d7.png)

![vue5](https://user-images.githubusercontent.com/58843821/112082761-3d6a5c00-8bc9-11eb-8e2b-8bf8839b4aa7.png)

 
