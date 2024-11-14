<template>
  <div>
    <!-- 버튼을 클릭하여 'show' 값을 토글한다.-->
    <button @click="show = !show">Toggle</button>
    <!-- fade 이름을 가진 트랜지션을 적용한다.-->
    <transition name="fade">
      <!-- 버튼이 클릭될 때마다 변경되는 'show'값으로 랜더링 여부를 결정한다.-->
      <!-- 랜더링이 될 때, fade 애니메이션이 발생한다. -->
      <p v-if="show">hello</p>
    </transition>
  </div>
</template>

<script>
export default {
  data() {
    return {
      show: true, // 초기값 설정
    };
  },
};
</script>

<style>
/* 각 클래스는 트랜지션에서 설정한 name이 접두어로 붙는다. (name = fade) */

/* 
Enter | Opacity : 0 -> Opacity : 1
Leave | Opacity : 1 -> Opacity : 0
*/

/* 트랜지션 진입 및 진출 애니메이션에 적용 */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s; /* 0.5초동안 opcity를 변경한다. */
}

/* 트랜지션의 시작과 종료 상태를 정의함 */
fade-enter,
.fade-leave-to {
  opacity: 0; /* 투명도를 0으로 설정함. */
}
</style>
