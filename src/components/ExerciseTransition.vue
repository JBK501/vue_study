<!-- 
1. v-enter-from
  1.1. 요소가 DOM에 처음 추가될 때의 시작 상태
  1.2. 요소가 삽입되기 전에 해당 클래스가 적용된다.
  예시 : opacity : 0 으로 설정하면, 요소가 보이지 않게 시작한다. => 보이지 않다가 보이는 애니메이션 적용가능

2. v-enter-active
  1.1. 요소가 DOM에 추가된 후, 애니메이션이 진행되는 동안 유지되는 클래스
  1.2. transition : opacity 0.5s ease; 로 설정하면, 불투명도가 0에서 1로 부드럽게 변화한다.

3. v-enter-to
  3.1. 요소가 DOM에 완전히 추가된 후, 최종 상태
  3.2. 요소가 삽입된 후 1프레임이 지나면 적용된다.
  3.3. opacity : 1 로 설정하면 요소가 완전히 보인다.

4. v-leave-from
  4.1. 요소가 DOM에서 제거되기 시작할 때의 시작 상태
  4.2. opacity : 1; 로 설정하면, 요소가 보이는 상태에서 시작한다. (보이다가 안보이기)  

5. v-leave-active
  5.1. 요소가 DOM에서 제거되는 동안 애니메이션이 진행되는 동안 진행되는 클래스
  5.2. transition: opacity 0.5s ease;로 설정하면, 요소의 불투명도가 서서히 사라진다.

6. v-leave-to
  6.1. 요소가 DOM에서 완전히 제거된 후의 최종상태
  6.2. opacity:0; 로 설정하면, 요소가 완전히 사라진다.
-->
<template>
  <div>
    <!-- 버튼을 클릭하여 'show' 값을 토글한다.-->
    <button @click="show = !show">Toggle</button>

    <!-- fade 이름을 가진 트랜지션을 적용한다.-->
    <transition name="fade">
      <p v-if="show">hello</p>
    </transition>

    <!-- slide fade -->
    <button @click="show2 = !show2">Toggle2</button>
    <transition name="slide-fade">
      <p v-if="show2">안녕</p>
    </transition>

    <!-- bounce -->
    <button @click="show3 = !show3">Toggle3</button>
    <transition name="bounce">
      <p v-if="show3" style="text-align: center">여기 텍스트 있어요!</p>
    </transition>
  </div>

  <!-- 클릭 시 상태변경 (수정 -> 저장 -> 취소)-->
  <span style="margin-right: 20px">클릭 시 상태 변경 : </span>
  <div class="btn-container">
    <transition name="slide-up">
      <button v-if="docState === 'saved'" @click="docState = 'edited'">
        수정
      </button>
      <button v-else-if="docState === 'edited'" @click="docState = 'editing'">
        저장
      </button>
      <button v-else-if="docState === 'editing'" @click="docState = 'saved'">
        취소
      </button>
    </transition>
  </div>

  <!-- 컴포넌트 간 트랜지션 -->
  <br /><br /><br />
  <!-- radio 버튼을 통해, activeComponent 값을 변경한다.-->
  <!-- value -> activeComponent 에 할당 -->
  <label for="">
    <input type="radio" v-model="activeComponent" value="ComA" />
  </label>
  <label for="">
    <input type="radio" v-model="activeComponent" value="ComB" />
  </label>
  <!-- activeComponent 값 변경에 따라 컴포넌트를 전환한다. -->
  <transition name="fade2" mode="out-in">
    <!-- 현재 활성화된 컴포넌트를 랜더링한다. -->
    <component :is="activeComponent"></component>
  </transition>
</template>

<script>
// import { Transition } from "vue";
import ComA from "./ComA.vue";
import ComB from "./ComB.vue";

export default {
  components: { ComA, ComB },
  data() {
    return {
      show: true, // 초기값 설정
      show2: true,
      show3: true,
      docState: "saved",
      activeComponent: "ComA",
    };
  },
};
</script>

<style>
/* 각 클래스는 트랜지션에서 설정한 name이 접두어로 붙는다. (name = fade) */

/* 트랜지션 진입 및 진출 애니메이션에 적용 */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s; /* 0.5초 동안 opacity를 변경한다. */
}

/* 요소가 화면에 나타나기 시작할 때의 초기상태 (나타나기 전에는 0이어야 함.) */
/* 요소가 화면에서 사라진 상태 (사라질 때는 0이어야 함.) */
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

/* slide fade */
.slide-fade-enter-active {
  transition: all 0.3s ease-out;
}

.slide-fade-leave-active {
  transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(20px);
  opacity: 0;
}

/* bounce */
.bounce-enter-active {
  animation: bounce-in 0.5s;
}

.bounce-leave-active {
  animation: bounce-in 0.5s reverse;
}

/*
0% : 애니메이션 시작 상태
50% : 애니메이션 중간지점. (본래크기보다 1.25배 크게 만듬으로써 바운스 효과발생)
100% : 애니메이션 최종 지점. (본래크기로 복귀)
*/
@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.25);
  }
  100% {
    transform: scale(1);
  }
}

/* 클릭 시 상태변경 (수정 -> 저장 -> 취소) */
.btn-container {
  display: inline-block;
  position: relative;
  height: 1em;
}

button {
  white-space: pre;
}

.slide-up-enter-active,
.slide-up-leave-active {
  transition: all 0.25s ease-out;
}

.slide-up-enter-from {
  opacity: 0;
  transform: translateX(30px);
}

.slide-up-leave-to {
  opacity: 0;
  transform: translateY(-30px);
}

/* 컴포넌트 간 트랜지션  */
.fade2-enter-active,
.fade2-leave-active {
  transition: opacity 0.5s ease;
}

.fade2-enter-from,
.fade2-leave-to {
  opacity: 0;
}
</style>
