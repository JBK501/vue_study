<template>
  <div id="app">
    <!-- NumberCounter 컴포넌트를 랜더링한다.-->
    <!-- <NumberCounter /> -->
    <!-- <ExerciseView01 /> -->
    <!-- <ExerciseVue02 /> -->
    <ExerciseVue03 />
  </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
// import NumberCounter from "./components/NumberCounter.vue";
// import ExerciseView01 from "./components/ExerciseVue01.vue";
// import ExerciseVue02 from "./components/ExerciseVue02.vue";
import ExerciseVue03 from "./components/ExerciseVue03.vue";

/*
App.vue 파일에서 내보내는(export) 컴포넌트는 main.js 파일에서 사용한다.
*/
export default {
  // 해당 컴포넌트 이름을 App으로 정의한다.
  name: "App",

  // components 옵션에 템플릿을 등록하면, 원하는 템플릿을 사용할 수 있다.
  components: {
    // HelloWorld,

    // NumberCounter 컴포넌트를 등록한다.
    // NumberCounter,
    // ExerciseView01,
    // ExerciseVue02,
    ExerciseVue03,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
