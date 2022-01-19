<template>
  <form class="product-detail-form" @submit.prevent="addToBasket">
    <SelectableAttributeList
      :selectableAttributes="productData.selectableAttributes"
      :productVariants="productData.productVariants"
    />
    <QuantitySection
      :model="model"
      @data="calculation($event)"
      :errorCheck="errorCheck"
      :errorMessage="errorMessage"
    />
    <ProductPriceGroup :totalPrice="model.totalPrice" />
    <div class="button-holder">
      <button type="submit" class="button is-secondary" :disabled="isDisabled">
        SEPETE EKLE
      </button>
      <span>Ödeme Yöntemleri</span>
    </div>
  </form>
</template>

<script>
import ProductPriceGroup from "@/components/ProductPriceGroup";
import QuantitySection from "@/components/QuantitySection";
import SelectableAttributeList from "@/components/SelectableAttributeList";

export default {
  name: "ProductDetailFrom",
  components: {
    ProductPriceGroup: ProductPriceGroup,
    QuantitySection: QuantitySection,
    SelectableAttributeList: SelectableAttributeList,
  },
  props: ["productData", "selectedVariant"],
  data() {
    return {
      model: {
        totalPrice: 0,
        stockQuantity: 10000,
        baremList: [],
      },
    };
  },
  created() {
    const baremList = this.productData.baremList;
    this.model.baremList = baremList;
    this.model.minPrice = baremList[0].price;
    this.model.minQuantity = baremList[0].minimumQuantity;
    this.model.maxQuantity = baremList[baremList.length - 1].maximumQuantity;
  },
  methods: {
    addToBasket() {
      const sendModel = {
        selectedVariant: this.selectedVariant,
        quantity: this.model.quantity,
        totalPrice: this.model.totalPrice,
      };
      console.log("sendModel", sendModel);
    },
    calculation(value) {
      this.model.quantity = value;
      let price = null;
      this.model.baremList.map((barem) => {
        if (value >= barem.minimumQuantity) {
          if (value <= barem.maximumQuantity) {
            price = barem.price;
          }
        }
      });
      if (value) {
        if (price) {
          this.model.totalPrice = (price * value).toFixed(2);
        } else {
          this.model.totalPrice = (this.model.minPrice * value).toFixed(2);
        }
      } else {
        this.model.totalPrice = this.model.minPrice;
      }
    },
  },
  computed: {
    isDisabled() {
      return false;
    },
    errorCheck() {
      if (this.model.quantity < this.model.minQuantity) {
        return true;
      }
      return false;
    },
    errorMessage() {
      if (this.model.quantity === "") {
        return "Bu alanın doldurulması zorunludur.";
      }
      if (this.model.quantity < this.model.minQuantity) {
        return `Bu alan ${this.model.minQuantity}'den az ${this.model.maxQuantity}'den fazla olmamalıdır.`;
      }
      return "";
    },
  },
};
</script>

<style scope>
.product-detail-form {
  float: left;
  width: 480px;
}
.button-holder {
  display: flex;
  align-items: center;
  width: 80%;
  margin: 15px 0 0 100px;
}
.button-holder > button {
  float: left;
  width: 180px;
  line-height: 45px;
  height: 46px;
  padding-bottom: 1px;
  font-weight: bold;
}
.button-holder > button:disabled {
  opacity: 0.5;
  -ms-filter: "progid:DXImageTransform.Microsoft.Alpha(Opacity=50)";
  filter: alpha(opacity=50);
  cursor: default;
}
.button-holder > span {
  margin-left: 10px;
  font-size: 12px;
  color: #0063cf;
  cursor: pointer;
}
</style>
