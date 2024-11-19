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
</template>

<script>
export default {
  data() {
    return {
      show: true, // 초기값 설정
      show2: true,
      show3: true,
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
</style>
