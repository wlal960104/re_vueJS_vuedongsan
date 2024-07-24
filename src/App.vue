<template>
  <!-- 상단 메뉴 -->
  <div class="menu">
    <a v-for="a in menu" :key="a">{{a}}</a> <!-- Home 3개 출력 -->
  </div>
  <!-- // 상단 메뉴 끝 -->

  <!-- 모달창 영역 -->
  <div class="black-bg" v-if="isModal === true">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세페이지내용임</p>
    </div>
  </div>
  <!-- // 모달창 영역 끝 -->

  <div v-for="(a,i) in products" :key="i">
    <img src="./assets/room0.jpg" alt="room_img">
    <h4>{{a}}</h4>
    <p>10만원</p>
    <button @click="increase(i)">허위매물신고</button><br>
    <span>신고수 : {{count[i]}}</span>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
      menu : ['Home', 'Shop', 'About'],
      count : [0,0,0],
      isModal : false
    }
  },
  methods: {
    increase(i) {
      // 함수 내용 입력
      this.count[i]++;
    }
  },
  components: {

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.menu {
  background : darkslateblue;
  padding : 15px;
  border-radius : 5px;
}
.menu a {
  color : white;
  padding : 10px;
}
body {
  margin : 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%; height:100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}
</style>
