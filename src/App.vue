<template>
  <div class="container">
    <div class="sections-holder">
      <ImageSection :images="images" />
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
    };
  },
  created() {
    let allImage = [];
    this.productData.productVariants.map((variant) =>
      variant.images.map((image) => allImage.push(image))
    );
    this.images = allImage;
    console.log(productDataJson);
  },
};
</script>

<style></style>
