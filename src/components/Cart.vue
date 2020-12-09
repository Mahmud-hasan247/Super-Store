<template>
  <div>
      <h2 class='text-center'>Cart</h2>
    <li class="list-group-item d-flex justify-content-between mb-3">
      <h6 class="">Name</h6>
      <h6 class="">Price</h6>
    </li>
    <ul class="list-group">
      <li
        v-for="(item, index) in items"
        :key="index"
        class=" list-group-item d-flex justify-content-between">
        <button @click='remove(index)' class='btn btn-sm btn-danger'>-</button>
        <p>{{ item.name }}</p>
        <p>{{ item.price }}</p>
      </li>
      
    </ul>
    <li v-if="totalPrice > 0" class="mt-3 list-group-item d-flex justify-content-between">
        <h6>Total</h6>
        <h6>{{ totalPrice }}</h6>
      </li>
  </div>
</template>

<script>
export default {
  props: ["items"],
  computed: {
      totalPrice() {
          let total = 0
          this.items.forEach(item => {
              total += parseFloat(item.price)
          })
          return total
      }
  },
  methods: {
      remove(index) {
          this.$emit('removeItem', index)
      }
  }
};
</script>
