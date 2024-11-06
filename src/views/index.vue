<template>
    <div class="Wrapper">
      <div class="Container">
        <CategoryComponent v-for="category in Categories" :key="category" 
        :color="category.color"  
        :name="category.name"
        :quantity="category.quantity"
        :picture="category.picture"
        />
      </div>
  
      <div class="PromotionContainer">
        <PromotionComponent v-for="promotion in Promotions" :key="promotion" 
        :color="promotion.color"  
        :text="promotion.text"
        :picture="promotion.picture"
        />
      </div>
    </div>
</template>

<script>
  import CategoryComponent from '../components/CategoryComponent.vue';
  import PromotionComponent from '../components/PromotionComponent.vue';
  import { RouterView } from 'vue-router';

  export default{
    components: {
        CategoryComponent,
        PromotionComponent
    },

    data() {
    return {
      Categories:[
        {
          color:"#F2FCE4",
          name:"Hamburger",
          quantity:"14 items",    
          picture: (new URL("@/assets/burger.png", import.meta.url))
        },
        {
          color:"#FFFCEB" ,
          name:"Peach",
          quantity:"17 items",    
          picture:(new URL("@/assets/persimmon.png", import.meta.url))
        },
        {
          color:"#ECFFEC" ,
          name:"Oganic Kiwi",
          quantity:"21 items",    
          picture:(new URL("@/assets/kiwi.png", import.meta.url))
        },
        {
          color:"#FEEFEA" ,
          name:"Red Apple",
          quantity:"68 items",    
          picture:(new URL("@/assets/apple.png", import.meta.url))
        },
        {
          color:"#FFF3EB" ,
          name:"Snack",
          quantity:"34 items",    
          picture:(new URL("@/assets/snack.png", import.meta.url))
        },
        {
          color:"#FFF3FF" ,
          name:"Black plum",
          quantity:"25 items",    
          picture:(new URL("@/assets/plum.png", import.meta.url))
        },
        {
          color:"#F2FCE4" ,
          name:"Vegetable",
          quantity:"65 items",    
          picture:(new URL("@/assets/cabbage.png", import.meta.url))
        },
        {
          color:"#FFFCEB" ,
          name:"Headphone",
          quantity:"33 items",    
          picture:(new URL("@/assets/headphone.png", import.meta.url))
        },

        {
          color:"#F2FCE4" ,
          name:"Cake & Milk",
          quantity:"54 items",    
          picture:(new URL("@/assets/snack2.png", import.meta.url))
        },
        {
          color:"#FFF3FF" ,
          name:"Orange",
          quantity:"63 items",    
          picture:(new URL("@/assets/orange.png", import.meta.url))
        }
      ],

      Promotions:[
        {
          color:"#F0E8D5",
          text:"Everyday Fresh & Clean with Our Products",
          picture:(new URL("@/assets/onion.png", import.meta.url))
        },
        {
          color:"#F3E8E8",
          text:"Make your Breakfast Healthy and Easy",
          picture:(new URL("@/assets/juice.png", import.meta.url))
        },
        {
          color:"#E7EAF3",
          text:"The best Organic Product Online",
          picture:(new URL("@/assets/vegetable.png", import.meta.url))
        },
      ],
    };
  },
  };


</script>

<style scoped>
.Wrapper{  
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  height: 100vh;
  width: 100vw;
  overflow: hidden;
  padding: 0px 20px;
}

.Container{
  width: 60%;
  display: flex;
  justify-content: space-evenly;
  margin-bottom: 40px;
}

.PromotionContainer{
  width: 60%;
  display: flex;
  justify-content: space-evenly;
}
</style>
