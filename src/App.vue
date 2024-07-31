<template>
  <!-- 모달창 영역 -->
  <transition name="fade">
    <Modal @closeModal="isModal = false" :prodList="prodList" :prodId="prodId" :isModal="isModal"/>
  </transition>
  <!-- 상단 메뉴 -->
  <div class="menu">
    <a v-for="a in menu" :key="a">{{a}}</a> <!-- Home 3개 출력 -->
  </div>
  <!-- // 상단 메뉴 끝 -->

  <!-- 할인 배너 영역 -->
  <Discount/>

  <button @click="priceSort">가격순 정렬</button>
  <button @click="sortBack">되돌리기</button>

  <!-- 여기 영역만 라우터로 뚫기 -->
  <!-- 상품 리스트 영역 -->
  <Card @report="increase($event)" @openModal="isModal = true; prodId = $event" v-for="(prodData,i) in prodList"
        :key="i" :prodData="prodData" :count="count[i]"/>
</template>

<script>
import prodList from './assets/prodData.js'
import Discount from "./components/Discount.vue";
import Modal from "./components/Modal.vue";
import Card from "@/components/Card.vue";
import discount from "@/components/Discount.vue";

export default {
  name: 'App',
  computed: {
    discount() {
      return discount
    }
  },
  // 데이터 저장 공간 (= state)
  data() {
    return {
      menu : ['Home', 'Shop', 'About'],
      count : [], // 신고 수
      isModal : false,
      originProdList : [...prodList], // 부동산 데이터 원본
      prodList : [...prodList], // 부동산 데이터들
      prodId : 0, // 상품 id
      showDiscount : true,
      discountNum : 20, // 할인률
    }
  },
  methods: {
    // [허위매물신고] 버튼 클릭 시 신고 수 증가
    increase(i) {
      // 함수 내용 입력
      this.count[i]++;
    },
    // 가격 정렬 기능
    priceSort() {
      this.prodList.sort(function(a,b) {
        return a.price -b.price;
      });
    },
    // 되돌리기 버튼 클릭 시
    sortBack() {
      this.prodList = [...this.originProdList];
    }
  },
  components: {
    Discount : Discount, // Discount 로 축약 가능 (ES6 문법)
    Modal : Modal, // Modal 로 축약 가능 (ES6 문법)
    Card
  },
  // 화면 랜딩 되기전 데이터 셋팅
  created() {
    console.log('App.vue ::: created > ')
    // 신고 수 초기화 (모두 0으로 초기화), DB 사용 시 초기화 불필요!
    this.prodList.forEach(() => {
      this.count.push(0);
    });
  },
  mounted() {
    console.log('App.vue ::: mounted > ')


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
.discount {
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
/* 시작 시 스타일 */
.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: all 1s;
}
/* 끝날 시 스타일 */
.fade-enter-to {
  opacity: 1;
}

/* 시작 시 스타일 */
.fade-leave-from {
  opacity: 1;
}
.fade-leave-active {
  transition: all 1s;
}
/* 끝날 시 스타일 */
.fade-leave-to {
  opacity: 0;
}


</style>
