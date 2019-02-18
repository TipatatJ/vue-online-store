<template>
  <div>
    <h1 class="wrapper">{{ pageTitle }}</h1>
    <ul class="wrapper item-grid">
      <li
        v-for="product in productsByGender"
        :key="product.id"
        class="item-grid__item"
      >
        <router-link :to="{ name: 'product', params: { id: product.id } }">
          <img
            class="product-image"
            :src="imagePath(product)"
            alt="product image"
          />
          <p class="product-title">{{ product.name }}</p>
          <p>
            <em>${{ product.price }}</em>
          </p> </router-link
        >}
      </li>
    </ul>
  </div>
</template>

<script>
import { imagePath } from "@/mixins/imagePath.js";

export default {
  name: "GenderOverview",
  mixins: [imagePath],
  computed: {
    gender() {
      return this.$route.params.gender;
    },
    pageTitle() {
      return `${this.gender[0].toUpperCase()}${this.gender.slice(1)}`;
    },
    productsByGender() {
      return this.$store.getters.productsByGender(this.gender);
    }
  }
};
</script>
