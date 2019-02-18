<template>
  <div class="wrapper">
    <h1>Cart</h1>
    <ul>
      <li v-for="item in cartItems" class="flex-col cart-list__item">
        <img :src="imagePath(item)" class="thumbnail" alt="product thumnail" />
        <div class="flex-col cart-list__item__details">
          <div>
            <p>{{ item.name }}</p>
            <p>Size: {{ item.size }}</p>
            <p>Color: {{ item.color }}</p>
          </div>
          <p>${{ item.price }}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
import { imagePath } from "@/mixins/imagePath.js";

export default {
  name: "cart",
  mixins: [imagePath],
  computed: {
    cartItems() {
      return this.$store.getters.cartItems;
    }
  }
};
</script>

<style>
.cart-list {
  width: 70%;
  margin-right: 1rem;
  @media only screen and (max-width: 832px) {
    width: 100%;
  }
}

.cart-list__item {
  width: 100%;
  border-bottom: 1px solid #2c3e50;
}

.cart-list__item__details {
  flex: 2;
  justify-content: space-between;
  margin-left: 2rem;
}

.thumbnail {
  max-width: 50px;
  margin-top: 0.5rem;
}
</style>
