<template>
  <fieldset class="price-cover">
    <label>Toplam</label>
    <div class="price-detail">
      <strong>{{ totalPrice }} TL</strong>
      <div>
        <small class="cargo-type">
          Kargo ücreti: <span>Alıcı Öder</span>
        </small>
      </div>
    </div>
  </fieldset>
</template>

<script>
export default {
  name: "ProductPriceGroup",
  props: ["totalPrice"],
};
</script>

<style scope>
.price-cover {
  margin-top: 10px;
  padding: 0 0 10px 13px;
}
.cargo-type {
  display: block;
  margin-top: 5px;
  margin-bottom: 11px;
  font-size: 12px;
  color: #424242;
}
.cargo-type > span {
  font-size: 12px;
  color: #0063cf;
  cursor: pointer;
}
.price-cover > label {
  float: left;
  font-weight: 500;
  width: 67px;
  margin-bottom: 0;
  font-size: 12px;
  color: #000;
  text-align: right;
  line-height: 29px;
  font-weight: bold;
  margin-top: -3px;
}
.price-detail {
  float: left;
  width: 384px;
  margin-left: 15px;
  position: relative;
}
.price-detail > strong {
  font-size: 18px;
  font-weight: 500;
}
</style>
