<template>

   <!-- 모달창 영역 -->
  <div class="black-bg" v-if="isModal === true">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세페이지내용임</p>
      <button @click="isModal=false">닫기</button>
    </div>
  </div>
  <!-- // 모달창 영역 끝 -->

  <!-- 상단 메뉴 -->
  <div class="menu">
    <a v-for="a in menu" :key="a">{{a}}</a> <!-- Home 3개 출력 -->
  </div>
  <!-- // 상단 메뉴 끝 -->

  <div v-for="(a,i) in prodList" :key="i">
    <img :src="`${a.image}`" alt="room_img" class="room-img">
    <h4 @click="isModal = true">{{a.title}}</h4>
    <p>{{a.price}}원</p>
    <button @click="increase(i)">허위매물신고</button><br>
    <span>신고수 : {{count[i]}}</span>
  </div>
</template>

<script>
import prodList from './assets/prodData.js'

export default {
  name: 'App',
  // 데이터 저장 공간 (= state)
  data() {
    return {
      menu : ['Home', 'Shop', 'About'],
      count : [0,0,0],
      isModal : false,
      prodList // 부동산 데이터들
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
.room-img {
  width: 100%;
  margin-top: 40px;
}
</style>
