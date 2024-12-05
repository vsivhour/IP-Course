<template>
  <div class="wrapper">
    <!-- Categories Section -->
    <div class="container">
      <CategoryComponent 
        v-for="category in categories" 
        :key="category.id"   
        :name="category.name"
        :productCount="category.productCount"
        :color="category.color"
        :image="category.image"
      />
    </div>

    <!-- Promotions Section -->
    <div class="promotion-container">
      <PromotionComponent 
        v-for="promotion in promotions" 
        :key="promotion.id"   
        :title="promotion.title"
        :url="promotion.url"
        :color="promotion.color"
        :buttonColor="promotion.buttonColor"
        :image="promotion.image"
      />
    </div>

    <!-- Menu & Products Section -->
    <div class="menu-products-container">
      <MenuComponent :categories="categories" @category-selected="filterProducts" />
      <ProductComponent :products="filteredProducts" />
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import CategoryComponent from '@/components/CategoryComponent.vue';
import PromotionComponent from '@/components/PromotionComponent.vue';
import MenuComponent from '@/components/MenuComponent.vue';
import ProductComponent from '@/components/ProductComponent.vue';
import { useProductStore } from '@/stores/product';
import { onMounted } from 'vue';
import { mapState } from 'pinia';

export default {
  components: {
    CategoryComponent,
    PromotionComponent,
    MenuComponent,
    ProductComponent
  },

  data() {
    return {
      selectedCategory: 'All'
    };
  },
  setup() {
    const productStore = useProductStore();
    return { productStore };
  },

  // computed: {
  //   filteredProducts() {
  //     return this.selectedCategory === 'All' 
  //       ? this.products 
  //       : this.products.filter(p => p.group === this.selectedCategory);
  //   }
  // },
  computed: {
    ...mapState(useProductStore, {
      groups: 'groups',
      categories: 'categories',
      promotions: 'promotions',
      products: 'products',
    }),
    filteredProducts() {
      return this.selectedCategory === 'All' 
        ? this.products 
        : this.products.filter(p => p.group === this.selectedCategory);
    }
  },
  async mounted() {
      await this.productStore.fetchGroups();
      await this.productStore.fetchCategories();
      await this.productStore.fetchPromotions();
      await this.productStore.fetchProducts();

      console.log('this.products', this.products)
  },
};

</script>

<style scoped>
.wrapper {  
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
}

.container {
  width: 100%;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  margin-bottom: 40px;
}

.promotion-container {
  width: 100%;
  display: flex;
  justify-content: space-between;
  margin-bottom: 40px;
}

.menu-products-container {
  width: 100%;
}

@media (max-width: 768px) {
  .container, .promotion-container {
    flex-direction: column;
    gap: 20px;
  }
}
</style>
