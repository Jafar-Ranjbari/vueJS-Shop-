<template>
    <div class="cart">
      <h1>Your Cart</h1>
      <div v-if="cartItems.length === 0">No items in cart.</div>
      <ul>
        <li v-for="item in cartItems" :key="item.id">
          {{ item.title }} - {{ item.price }} $
          <button @click="removeFromCart(item.id)">Remove</button>
        </li>
      </ul>
      <h2>Total: {{ cartTotal }} $</h2>
    </div>
  </template>
  
  <script lang="ts">
  import { defineComponent, ref } from 'vue';
  
  export default defineComponent({
    name: 'Cart',
    setup() {
      const cartItems = ref<any[]>([]);
      const cartTotal = ref<number>(0);
  
      const addToCart = (item: any) => {
        cartItems.value.push(item);
        cartTotal.value += item.price;
      };
  
      const removeFromCart = (id: number) => {
        const index = cartItems.value.findIndex(item => item.id === id);
        if (index !== -1) {
          cartTotal.value -= cartItems.value[index].price;
          cartItems.value.splice(index, 1);
        }
      };
  
      return { cartItems, cartTotal, addToCart, removeFromCart };
    }
  });
  </script>
  
  <style lang="scss" scoped>
  .cart {
    text-align: center;
  
    ul {
      list-style-type: none;
      padding: 0;
  
      li {
        display: flex;
        justify-content: space-between;
        margin-bottom: 10px;
      }
    }
  }
  </style>
  