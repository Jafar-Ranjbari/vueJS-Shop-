<template>
    <div class="product-card">
      <img :src="product.image" :alt="product.title" />
      <h2>{{ product.title }}</h2>
      <p>{{ product.price }} $</p>
      <button @click="$emit('addToCart', product)">Add to Cart</button>
    </div>
  </template>
  
  <script lang="ts">
  import { defineComponent, PropType } from 'vue';
  
  export default defineComponent({
    name: 'ProductCard',
    props: {
      product: {
        type: Object as PropType<{ id: number; title: string; image: string; price: number }>,
        required: true,
      },
    },
  });
  </script>
  
  <style lang="scss" scoped>
  .product-card {
    border: 1px solid #ddd;
    padding: 20px;
    margin: 10px;
    max-width: 200px;
  
    img {
      width: 100%;
      height: 150px;
      object-fit: cover;
    }
  
    h2 {
      font-size: 1.2em;
    }
  }
  </style>
  