<template>
  <li class="thumbnail-item" @click="updateImage(item)">
    <img :class="{ selected: isSelected === item }" :src="item" />
  </li>
</template>

<script>
export default {
  name: "ThumbnailItem",
  props: ["item", "updateImage", "isSelected"],
};
</script>

<style scope>
.thumbnail-item {
  display: inline-block;
  margin-left: 7px;
  cursor: pointer;
}
.thumbnail-item:first-of-type {
  margin-left: 0;
}
img {
  width: 60px;
  height: 60px;
  border: 1px solid #eee;
}
.selected {
  border: solid 2px #616161;
}
</style>
