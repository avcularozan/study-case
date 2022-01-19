<template>
  <div class="attribute-item">
    <input
      type="radio"
      :value="item"
      :name="name"
      :id="item"
      @change="changeAttribute(name, item)"
      :disabled="isDisabled"
    />
    <label :for="item">{{ item }}</label>
  </div>
</template>

<script>
export default {
  name: "AttributeItem",
  props: ["item", "name", "changeAttribute", "selectableListe"],
  computed: {
    isDisabled() {
      if (this.selectableListe) {
        return !this.selectableListe.includes(this.item);
      }
      return false;
    },
  },
};
</script>

<style>
.attribute-item {
  float: left;
  margin-left: 12px;
  position: relative;
}
.attribute-item:nth-of-type(3n + 1) {
  margin-left: 0;
}
.attribute-item:nth-of-type(n + 4) {
  margin-top: 8px;
}
.attribute-item input[type="radio"] {
  position: absolute;
  left: -9999px;
}
.attribute-item input[type="radio"] + label {
  display: block;
  width: 120px;
  margin-bottom: 0;
  font-size: 13px;
  font-weight: 400;
  text-align: center;
  line-height: 31px;
  cursor: pointer;
  border: 2px solid #e0e0e0;
  border-radius: 2px;
  white-space: nowrap;
  overflow: hidden;
  -o-text-overflow: ellipsis;
  text-overflow: ellipsis;
  padding: 1px 5px 0;
}
.attribute-item input[type="radio"] + label:hover {
  border-color: #bdbdbd;
}
.attribute-item input[type="radio"] + label:before {
  content: unset;
  position: unset;
}
.attribute-item input[type="radio"]:checked + label {
  border-width: 2px;
  line-height: 31px;
  border-color: #147ec4;
  background-color: #edf4fb;
  font-weight: bold;
  padding-top: 1px;
}
.attribute-item input[type="radio"]:disabled + label {
  cursor: default;
  color: #e0e0e0;
  border-color: #eee;
  background-color: #fafafa;
}
</style>
