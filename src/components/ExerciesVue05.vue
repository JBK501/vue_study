<template>
  <!-- 폼 입력 바인딩 -->
  <!-- 
    1. v-model 은 양방향 데이터 바인딩 작업을 한다.
    2. v-model 은 form 엘리먼트 초기 값을 무시한다.
     2.1. 'value', 'selected', 'checked'
    3. 따라서 data 옵션 안에 있는 Javascript에서 초기값을 선언해야 한다. 

    [input:type 별 v-model 이 사용하는 값과 이벤트]
    1. text, textarea -> value 데이터, input 이벤트
    2. checkbox, radio -> checked 속성, change 이벤트
    3. Select 태그 -> value 를 prop로, change 이벤트
   -->

  <!-- type : text-->
  <input v-model="message" placeholder="여기를 수정해보세요." />
  <p>메시지 : {{ message }}</p>

  <!-- type : textarea-->
  <span>여러 줄을 가지는 메시지 :</span>
  <p style="white-space: pre-line">{{ message }}</p>
  <br />
  <textarea v-model="message" placeholder="여러줄을 입력해보세요."></textarea>

  <!-- type : checkbox -->
  <div id="example-3">
    <input type="checkbox" id="jack" value="Jack" v-model="checkedNames" />
    <label for="jack">Jack</label>
    <input type="checkbox" id="john" value="John" v-model="checkedNames" />
    <label for="john">John</label>
    <input type="checkbox" id="mike" value="Mike" v-model="checkedNames" />
    <label for="mike">Jack</label>
    <br />
    <span>체크한 이름 : {{ checkedNames }}</span>
  </div>

  <!-- type : radio -->
  <input type="radio" id="one" value="One" v-model="picked" />
  <label for="one">One</label>
  <br />
  <input type="radio" id="two" value="Two" v-model="picked" />
  <label for="two">Two</label>
  <br />
  <span>선택 : {{ picked }}</span>

  <!-- Select -->
  <select v-model="selected">
    <!--  사용하지 않는 옵션에는 빈값 넣기 -->
    <option disabled value="">Please select one</option>
    <option>A</option>
    <option>B</option>
    <option>C</option>
  </select>
  <span>선택함: {{ selected }}</span>

  <!-- Mutiple Select -->
  <select v-model="selecteds" multiple>
    <option>A</option>
    <option>B</option>
    <option>C</option>
  </select>
  <br />
  <span>Selected: {{ selecteds }}</span>

  <!-- 동적 Select 옵션 렌더링  -->
  <select v-model="selectedM">
    <option
      v-for="(option, index) in options"
      :key="index"
      v-bind:value="option.value"
    >
      {{ option.text }}
    </option>
  </select>
</template>

<script>
export default {
  data() {
    return {
      message: "",
      checked: "false",
      checkedNames: [],
      picked: "",
      selected: "",
      selecteds: [],
      selectedM: "A",
      options: [
        { text: "One", value: "A" },
        { text: "Two", value: "B" },
        { text: "Three", value: "C" },
      ],
    };
  },
};
</script>
