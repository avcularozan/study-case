<template>
  <div class="barem-item" :class="{ 'checked': isChecked }">
    <label>
      {{ getQuantityRange }}
      <br />
      <span>{{ getPrice }}</span>
    </label>
  </div>
</template>

<script>
export default {
  name: "BaremItem",
  props: ["baremItem", "quantity"],
  computed: {
    getQuantityRange() {
      return `${this.baremItem.minimumQuantity} - ${this.baremItem.maximumQuantity}`;
    },
    getPrice() {
      return `${this.baremItem.price} TL`;
    },
    isChecked() {
      if (this.quantity >= this.baremItem.minimumQuantity) {
        if (this.quantity <= this.baremItem.maximumQuantity) {
          return true;
        }
      }
      return false;
    },
  },
};
</script>

<style>
.barem-item {
  float: left;
  width: 94px;
  border-left: 1px solid #e0e0e0;
  letter-spacing: -0.4px;
  min-height: 48px;
  position: relative;
}
.barem-item:first-child {
  margin-left: 0;
}
.barem-item > label {
  display: block;
  margin-bottom: 0;
  padding: 7px 5px 5px;
  font-size: 12px;
  line-height: 16px;
  font-weight: normal;
  color: #616161;
}
.barem-item > label > span {
  display: block;
  font-weight: bold;
  color: #000;
  font-size: 13px;
  margin-top: 2px;
}
.checked {
  font-weight: 400;
  background-color: #ffedb9;
}
</style>
