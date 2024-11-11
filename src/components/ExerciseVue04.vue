<template>
  <!-- Default Event-->
  <div id="example-1">
    <button v-on:click="counter += 1">Add 1</button>
    <p>위 버튼을 클릭한 횟수는 {{ counter }} 번 입니다.</p>
  </div>

  <!-- 메소드 이벤트 핸들러 -->
  <div class="example-2">
    <button v-on:click="greet">Greet</button>
  </div>

  <!-- 인라인 메소드 핸들러 -->
  <div id="example-3">
    <button v-on:click="say('hi')">Say hi</button>
    <button v-on:click="say('what')">Say What</button>
  </div>
</template>

<!-- 이벤트 수식어 -->
<!-- 클릭 이벤트 중단 -->
<a href="" v-on:click.stop="doThis"></a>
<!-- submit 이벤드 중단 = event.preventDefault() -->
<form action="" v-on:submit.prevent="onSubmit"></form>
<!-- 이벤트 수식어 체이닝 -->
<a href="" v-on:click.stop.prevent="doThat"></a>
<!-- 이벤트 캡처 -->
<div v-on:click.capture="doThis">...</div>
<!-- 트리거 처리 -->
<div v-on:click.self="doThat">...</div>

<script>
export default {
  data() {
    return {
      // ex1
      counter: 0,
      // ex2
      name: "Vue.js",
    };
  },
  methods: {
    // ex2
    greet: function (event) {
      // 메소드 안에서 사용하는 'this' 는 Vue 인스턴스를 가리킨다.
      alert("Hello " + this.name + "!");

      // 'event' 는 네이티브 DOM 이벤트다.
      if (event) {
        alert(event.target.tagName);
      }
    },
    // ex3
    say: function (message) {
      alert(message);
    },
  },
};
</script>
