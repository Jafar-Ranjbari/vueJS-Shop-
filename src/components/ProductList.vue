
<template>
    <div class="product-list">
      <h1>Product List</h1>
      <div v-if="loading" class="loading">Loading...</div>
      <div v-else class="products">
        <ProductCard
          v-for="product in products"
          :key="product.id"
          :product="product"
          @addToCart="addToCart"
        />
      </div>
    </div>
  </template>
  
  <script lang="ts">
  import { defineComponent, ref, onMounted } from 'vue';
  import { fetchProducts } from '@/services/api';
  import ProductCard from '@/components/ProductCard.vue';
  
  export default defineComponent({
    name: 'ProductList',
    components: { ProductCard },
    setup() {
      const products = ref<any[]>([]);
      const loading = ref(true);
  
      const loadProducts = async () => {
        try {
          products.value = await fetchProducts();
        } catch (error) {
          console.error('Error loading products');
        } finally {
          loading.value = false;
        }
      };
  
      const addToCart = (product: any) => {
        console.log('Adding to cart:', product);
        // Implement cart logic or emit to parent
      };
  
      onMounted(() => {
        loadProducts();
      });
  
      return { products, loading, addToCart };
    },
  });
  </script>
  
  <style lang="scss" scoped>
  .product-list {
    text-align: center;
  
    .products {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
    }
  }
  </style>
  