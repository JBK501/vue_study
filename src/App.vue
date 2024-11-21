<template>
  <div id="app">
    <!-- 컴포넌트를 랜더링한다.-->
    <!-- <HelloWorld msg="Hello World Vue." /> -->
    <!-- <NumberCounter /> -->
    <!-- <ExerciseView01 /> -->
    <!-- <ExerciseVue02 /> -->
    <!-- <ExerciseVue03 /> -->
    <!-- <ExerciseVue04 /> -->
    <!-- <ExerciesVue05 /> -->

    <!-- props 예제 -->
    <!-- <input v-model="parentMsg" /> -->
    <!-- <ExerciseComponent01 v-bind:my-message="parentMsg" /> -->
    <!-- <ExerciseComponent01 v-bind="todo" /> -->

    <!-- 트랜지션 예제 -->
    <!-- <ExerciseTransition /> -->
    <!-- <ExerciseTransitionGroup /> -->

    <!-- Keep Alive 예제 -->
    <!-- <ExerciseKeepAlive /> -->

    <!-- Teleport 예제 (뷰에서 모달 사용) -->
    <ExerciseTeleport />
    <!-- <MyModal /> -->
  </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
// import NumberCounter from "./components/NumberCounter.vue";
// import ExerciseView01 from "./components/ExerciseVue01.vue";
// import ExerciseVue02 from "./components/ExerciseVue02.vue";
// import ExerciseVue03 from "./components/ExerciseVue03.vue";
// import ExerciseVue04 from "./components/ExerciseVue04.vue";
// import ExerciesVue05 from "./components/ExerciesVue05.vue";
// import ExerciseComponent01 from "./components/ExerciseComponent01.vue";
// import ExerciseTransition from "./components/ExerciseTransition.vue";
// import ExerciseTransitionGroup from "./components/ExerciseTransitionGroup.vue";
// import ExerciseKeepAlive from "./components/ExerciseKeepAlive.vue";
import ExerciseTeleport from "./components/ExerciseTeleport.vue";
// import MyModal from "./components/MyModal.vue";

/*
App.vue 파일에서 내보내는(export) 컴포넌트는 main.js 파일에서 사용한다.
*/
export default {
  // 해당 컴포넌트 이름을 App으로 정의한다.
  name: "App",

  data() {
    return {
      // props 테스트 데이터
      parentMsg: "",
      todo: {
        text: "Learn Vue",
        isComplete: false,
      },
    };
  },

  // components 옵션에 템플릿을 등록하면, 원하는 템플릿을 사용할 수 있다.
  components: {
    // HelloWorld,

    // NumberCounter 컴포넌트를 등록한다.
    // NumberCounter,
    // ExerciseView01,
    // ExerciseVue02,
    // ExerciseVue03,
    // ExerciseVue04,
    // ExerciesVue05,
    // ExerciseComponent01,
    // ExerciseTransition,
    // ExerciseTransitionGroup,
    // ExerciseKeepAlive,
    ExerciseTeleport,
    // MyModal, // 테스트용
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
