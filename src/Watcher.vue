<template>
  <input type="text" name="quantity" v-model="product.quantity" />
  <div>Total = (price * quantity)= {{ total }}</div>
</template>

<script setup>
import { ref, reactive, watch } from 'vue'
let total = ref(0)
let product = reactive({
  quantity: 0,
  price: 10
})

watch(()=>{ return {...product}}, (newVal, oldVal) => {
  console.log("newVal : ",newVal)
  console.log("oldVal : ", oldVal)
  total.value = newVal.quantity*newVal.price;
},{deep:true})
</script>

<style scoped>
</style>