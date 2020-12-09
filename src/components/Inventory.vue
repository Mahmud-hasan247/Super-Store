<template>
<div class='d-flex flex-wrap'>
  <div v-for="(item, index) in items" :key="index" class="card m-1 p-2" style="width: 16rem">
    <img :src="item.image" class="card-img-top" alt="..." />
    <div class="card-body">
      <h5 class="card-title"> {{ item.name }} </h5>
      <p class="card-text">
        Some quick example text to build on the card title and make up the bulk
        of the card's content.
      </p>
      <h5>$ {{ item.price }}</h5>
      <a @click="addToCart(item)" class="btn btn-primary">Add to cart</a>
    </div>
  </div>
</div>
</template>

<script>
export default {
  props: [ 'items' ],
  methods: {
    addToCart(item) {
      this.$emit("newCartItem", item)
    }
  }
};
</script>