<template>
  <div id="selectable-attributes">
    <div class="attribute-box">
      <label class="attribute-name">{{ selectableAttributes[0].name }}</label>
      <div class="attribute-holder">
        <AttributeItem
          v-for="value in selectableAttributes[0].values"
          :item="value"
          :key="value"
          :name="selectableAttributes[0].name"
          :changeAttribute="changeAttribute"
        />
      </div>
    </div>
    <div class="attribute-box">
      <label class="attribute-name">{{ selectableAttributes[1].name }}</label>
      <div class="attribute-holder">
        <AttributeItem
          v-for="value in selectableAttributes[1].values"
          :item="value"
          :key="value"
          :name="selectableAttributes[1].name"
          :changeAttribute="changeAttribute"
          :selectableListe="selectableListe"
        />
      </div>
    </div>
  </div>
</template>

<script>
import AttributeItem from "@/components/AttributeItem";

export default {
  name: "SelectableAttributeList",
  components: {
    AttributeItem: AttributeItem,
  },
  data() {
    return {
      attribute1: null,
      attribute2: null,
    };
  },
  props: ["selectableAttributes", "productVariants"],
  inject: ["updateAttribute"],
  methods: {
    changeAttribute(name, item) {
      if (this.selectableAttributes[0].name === name) {
        this.attribute1 = item;
      }
      if (this.selectableAttributes[1].name === name) {
        this.attribute2 = item;
      }
      if (this.attribute1 && this.attribute2) {
        this.updateAttribute(this.attribute1, this.attribute2);
      }
    },
  },
  computed: {
    selectableListe() {
      let test = [];
      this.productVariants.map((variant) => {
        if (variant.attributes[1].value === this.attribute1) {
          test.push(variant.attributes[0].value);
        }
      });
      return test;
    },
  },
};
</script>

<style scope>
.attribute-box {
  padding-left: 10px;
  margin-bottom: 12px;
  zoom: 1;
}
.attribute-box:before,
.attribute-box:after {
  content: "";
  display: table;
}
.attribute-box:after {
  clear: both;
}
.attribute-name {
  float: left;
  margin-bottom: 0;
  width: 70px;
  font-size: 12px;
  font-weight: 300;
  height: 36px;
  padding-top: 11px;
  color: #212121;
  text-align: right;
  font-weight: bold;
}
.attribute-holder {
  float: left;
  width: 402px;
  max-height: 142px;
  margin-left: 15px;
  overflow-y: auto;
  padding-right: 0px;
  margin-right: -32px;
  overflow-x: hidden;
}
</style>
