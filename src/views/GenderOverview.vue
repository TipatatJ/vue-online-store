<template>
  <div>
    <h1 class="wrapper">{{ pageTitle }}</h1>
    <ul>
      <li v-for="product in productsByGender">{{ product.name }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "GenderOverview",
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
