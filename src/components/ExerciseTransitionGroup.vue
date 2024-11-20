<script>
import { shuffle } from "lodash-es";

const getInitialItems = () => [1, 2, 3, 4, 5]; // 초기아이템을 배열로 반환하는 메서드
let id = getInitialItems().length + 1; // 아이템의 id값 저장

export default {
  data() {
    return {
      items: getInitialItems(),
    };
  },
  methods: {
    // 랜덤 index 에 아이템을 삽입하는 메서드
    insert() {
      const i = Math.round(Math.random() * this.items.length); // 랜덤 인덱스를 생성한다.
      this.items.splice(i, 0, id++); // 해당 인덱스에 새로운 아이템을 추가한다.
    },
    // 아이템 리스트를 초기 상태로 리셋하는 메서드
    reset() {
      this.items = getInitialItems(); // 초기 아이템 배열로 재설정한다.
    },
    // 아이템 리스트를 무작위로 섞는 메서드
    shuffle() {
      this.items = shuffle(this.items);
    },
    // 특정 아이템을 리스트에서 제거하는 메서드
    remove(item) {
      // 제거할 아이템의 index를 찾는다.
      const i = this.items.indexOf(item);
      if (i > -1) {
        // 찾았다면
        this.items.splice(i, 1); // 제거한다.
      }
    },
  },
};
</script>

<template>
  <button @click="insert">insert at random index</button>
  <button @click="reset">reset</button>
  <button @click="shuffle">suffle</button>

  <!-- 리스트 항목에 트랜지션 효과를 적용한다. -->
  <!-- tag="ul" => ul 태그로 랜더링 한다. -->
  <TransitionGroup tag="ul" name="fade" class="container">
    <div v-for="item in items" class="item" :key="item">
      {{ item }}
      <button @click="remove(item)">X</button>
    </div>
  </TransitionGroup>
</template>

<style>
.container {
  position: relative; /* 자식 요소를 절대위치 지정하기위해 설정함 */
  padding: 0;
}

.item {
  width: 100%;
  height: 30px;
  background-color: #f3f3f3;
  border: 1px solid #666;
  box-sizing: border-box; /* 테두리를 포함한 크기 계산 */
}

.fade-move,
.fade-enter-active,
.fade-leave-active {
  transition: all 0.5s cubic-bezier(0.55, 0, 0.1, 1);
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: scaleY(0.01) translate(30px, 0);
}

/* 사라지는 요소의 위치를 절대적으로 설정하여, 자연스러운 애니메이션 효과를 제공한다. */
.fade-leave-active {
  position: absolute;
}
</style>
