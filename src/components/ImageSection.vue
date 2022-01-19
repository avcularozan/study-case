<template>
  <div class="image-holder">
    <div class="image-contain">
      <img class="image-obj" :src="selectedImage" />
    </div>
    <div class="image-list">
      <ul>
        <ThumbnailItem
          v-for="image in imageList"
          :key="image"
          :item="image"
          :updateImage="updateImage"
          :isSelected="selected"
        />
      </ul>
    </div>
  </div>
</template>

<script>
import ThumbnailItem from "@/components/ThumbnailItem";
export default {
  name: "ImageSection",
  components: {
    ThumbnailItem: ThumbnailItem,
  },
  props: ["images"],
  data() {
    return {
      selectedImage: null,
    };
  },
  computed: {
    selected() {
      return this.selectedImage;
    },
    imageList() {
      return [...new Set(this.images)];
    },
  },
  methods: {
    updateImage(image) {
      this.selectedImage = image;
    },
  },
  created() {
    this.selectedImage = this.images[0];
  },
  watch: {
    images: function (newVal) {
      this.selectedImage = newVal[0];
    },
  },
};
</script>

<style>
.image-holder {
  position: relative;
  float: left;
  width: 450px;
}
.image-contain {
  height: 450px;
  width: 450px;
  margin-bottom: 30px;
  overflow: hidden;
  cursor: crosshair;
  position: relative;
}
.image-obj {
  position: absolute;
  top: 0;
  bottom: 0;
  margin: auto;
  width: 100%;
  height: auto;
}
.image-list {
  float: left;
  width: 400px;
  height: 70px;
  overflow: hidden;
}
ul {
  float: left;
  overflow-x: auto;
  overflow-y: hidden;
  width: 400px;
  height: 70px;
  white-space: nowrap;
}
</style>
