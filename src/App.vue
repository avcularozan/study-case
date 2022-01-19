<template>
  <div class="container">
    <div class="sections-holder">
      <ImageSection :images="images" />
      <div class="product-container">
        <div class="product-title">
          <h1>{{ title }}</h1>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import productDataJson from "../product-data";
import ImageSection from "@/components/ImageSection";

export default {
  name: "App",
  components: {
    ImageSection: ImageSection,
  },
  data() {
    return {
      productData: productDataJson,
      images: [],
      title: null,
    };
  },
  created() {
    let allImage = [];
    this.productData.productVariants.map((variant) =>
      variant.images.map((image) => allImage.push(image))
    );
    this.images = allImage;
    this.title = this.productData.productTitle;
    console.log(productDataJson);
  },
};
</script>

<style scope>
.product-container {
  width: 55%;
  float: left;
  padding: 15px 0 20px 20px;
}
.product-title {
  position: relative;
  width: 500px;
  padding-left: 10px;
  font-size: 22px;
  max-width: 500px;
  padding-right: 20px;
}
.product-detail-box {
  float: left;
  margin-top: 16px;
  position: relative;
}
</style>
