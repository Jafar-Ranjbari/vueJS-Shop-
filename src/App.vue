<template>
  <div id="app">
    <ProductList />
    <Cart />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import ProductList from '@/components/ProductList.vue';
import Cart from '@/components/Cart.vue';

export default defineComponent({
  name: 'App',
  components: { ProductList, Cart },
});
</script>

<style lang="scss">
#app {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin-top: 20px;
}
</style>
