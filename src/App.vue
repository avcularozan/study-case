<template>
  <div class="container">
    <div class="sections-holder">
      <ImageSection :images="images" />
      <div class="product-container">
        <div class="product-title">
          <h1>{{ title }}</h1>
        </div>
        <div class="product-detail-box">
          <ProductDetailInfo :price="price" :piece="piece" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import productDataJson from "../product-data";
import ImageSection from "@/components/ImageSection";
import ProductDetailInfo from "@/components/ProductDetailInfo";

export default {
  name: "App",
  components: {
    ImageSection: ImageSection,
    ProductDetailInfo: ProductDetailInfo,
  },
  data() {
    return {
      productData: productDataJson,
      images: [],
      title: null,
      price: null,
      piece: null,
    };
  },
  created() {
    let allImage = [];
    this.productData.productVariants.map((variant) =>
      variant.images.map((image) => allImage.push(image))
    );
    this.images = allImage;
    this.title = this.productData.productTitle;
    this.piece = this.productData.baremList[0].minimumQuantity;
    this.price = this.getPrice();
    console.log(productDataJson);
  },
  methods: {
    getPrice() {
      const baremList = this.productData.baremList;
      const firstPrice = baremList[0].price;
      const lastPrice = baremList[baremList.length - 1].price;
      return `${lastPrice} TL - ${firstPrice} TL`;
    },
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
