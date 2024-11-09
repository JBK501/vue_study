<!--
    ● 디렉티브(v-*) : 뷰에서 제공하는 HTML 속성
    ● v-html 
        - html코드를 그대로 출력한다.
        - XSS 공격에 취약할 수 있으므로, 신뢰할 수 있는 콘텐츠에만 사용해야 합니다.
    ● v-bind(: ) 
        - html 속성을 동적으로 바인딩한다. (Vue 데이터가 변경될 때, html 속성도 자동으로 변경된다.)   
        - <img v-bind:src="imageUrl">
        - <img :src="imageUrl">
    ● v-if
    ● v-on(@)
-->
<template>
  <p>{{ rawHtml }}</p>
  <p>html 디렉티브 : <span v-html="rawHtml"></span></p>
  <p v-if="seen">이제 이것을 볼 수 있습니다.</p>

  <a href="" v-on:click="dosomething">v-on</a><br />
  <a href="" @click="dosomething">v-on단축</a>
</template>

<script>
export default {
  data() {
    return {
      // {{}} mustache 구문 사용시, html 문자열 그대로 출력됨.
      // v-html 사용시, 빨간색으로 출력됨.
      rawHtml: "<span style='color:red'>빨간색 출력</span>",

      // v-if 에 적용
      seen: "true",
      //   seen: "",
    };
  },
};
</script>
