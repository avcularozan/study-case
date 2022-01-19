<template>
  <div class="info-box">
    <div class="order-price">
      <strong>
        <span>{{ price }}</span>
      </strong>
      <span> / Adet</span>
    </div>
    <span class="order-piece">
      <span>{{ piece }}</span>
      <span> Adet (Minimum Sipariş Adedi)</span>
    </span>
  </div>
</template>

<script>
export default {
  name: "ProductDetailInfo",
  props: ["price", "piece"],
};
</script>

<style scope>
.info-box {
  padding-left: 10px;
  margin-bottom: 13px;
}
.info-box .order-price {
  margin-bottom: 3px;
}
.info-box .order-price > strong {
  font-size: 24px;
  font-weight: bold;
}
.info-box .order-price > span {
  font-size: 12px;
  color: #757575;
}
.info-box .order-piece {
  color: #757575;
  font-weight: normal;
  font-size: 12px;
}
</style>
