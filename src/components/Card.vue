<template>
  <div class="card shadow-sm">
    <span class="img" :style="{backgroundImage: `url(${item.imgPath})`}" />
<!--    <img :src="item.imgPath" />-->
    <div class="card-body">
      <p class="card-text">
        <span>{{ item.name }}</span>&nbsp;
        <span class="discount badge bg-danger">{{ item.discountPer }} %</span>
      </p>
      <div class="d-flex justify-content-between align-items-center">
        <!-- button.btn.primary 후 tab을 눌러 자동 완성하였음 -->
        <button class="btn primary">구입하기</button>

<!--        <div class="btn-group">-->
<!--          <button type="button" class="btn btn-sm btn-outline-secondary">View</button>-->
<!--          <button type="button" class="btn btn-sm btn-outline-secondary">Edit</button>-->
<!--        </div>-->
        <small class="price text-muted">{{ lib.getNumberFormatted(item.price) }} 원</small>
        <small class="real text-danger">{{ lib.getNumberFormatted(item.price - (item.price * item.discountPer / 100)) }} 원</small>
      </div>
    </div>
  </div>
</template>
<script>
  import lib from "@/scripts/lib";

  export default {
    name: 'Card',
    props: {
      item: Object,
    },
    setup() {
      return {lib}
    }
  }
</script>

<style scoped>
.card .img {
  display: inline-block;
  width: 100%;
  height: 380px;
  background-size: cover;
  background-position: center;
}

.card .card-body .price {
  text-decoration: line-through;
}
</style>