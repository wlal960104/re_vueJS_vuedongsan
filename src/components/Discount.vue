<template>
  <div class="discount">
    <h4>지금 결제하면 {{discountNum}}% 할인</h4>
  </div>
</template>

<script>
export default {
  name: 'Discount',
  data () {
    return {
      discountNum : 10
    }
  },
  created() {
    console.log('Discount.vue ::: created > ')

  },
  mounted() {
    console.log('Discount.vue ::: mounted > ')

    // 1초에 1% 감소, 0되면 stop
    const decNum = setInterval(() => {
      this.discountNum--;
      if (this.discountNum === 0) {
        clearInterval(decNum);
      }
    }, 1000);
  }

}
</script>

<style>

</style>