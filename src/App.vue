<script setup>
import CategoryCard from './components/CategoryCard.vue'
import PromotionCard from './components/PromotionCard.vue'

// Import images
import burgerImg from './components/burger.png'
import peachImg from './components/peach.png'
import kiwiImg from './components/kiwi.png'
import appleImg from './components/apple.png'
import snackImg from './components/snack.png'
import plumImg from './components/blackplum.png'
import cabbageImg from './components/cabbage.png'
import headphoneImg from './components/headphone.png'
import cakeImg from './components/cake.png'
import orangeImg from './components/orange.png'
import onionImg from './components/onion.png'
import yogurtImg from './components/yogurt.png'
import vegetableImg from './components/vegetable.png'

const categories = [
  {
    title: 'Cake & Milk',
    items: 14,
    bgColor: '#F2FCE4',
    image: burgerImg,
  },
  {
    title: 'Peach',
    items: 17,
    bgColor: '#FFFCEB',
    image: peachImg,
  },
  {
    title: 'Organic Kiwi',
    items: 21,
    bgColor: '#ECFFEC',
    image: kiwiImg,
  },
  {
    title: 'Red Apple',
    items: 68,
    bgColor: '#FEEFEA',
    image: appleImg,
  },
  {
    title: 'Snack',
    items: 34,
    bgColor: '#FFF3EB',
    image: snackImg,
  },
  {
    title: 'Black plum',
    items: 25,
    bgColor: '#FFF3FF',
    image: plumImg,
  },
  {
    title: 'Vegetables',
    items: 65,
    bgColor: '#F2FCE4',
    image: cabbageImg,
  },
  {
    title: 'Headphone',
    items: 33,
    bgColor: '#FFFCEB',
    image: headphoneImg,
  },
  {
    title: 'Cake & Milk',
    items: 54,
    bgColor: '#F2FCE4',
    image: cakeImg,
  },
  {
    title: 'Orange',
    items: 63,
    bgColor: '#FFF3FF',
    image: orangeImg,
  },
]

const promotions = [
  {
    title: 'Everyday Fresh & Clean with Our Products',
    bgColor: '#F0E8D5',
    image: onionImg,
    buttonColor: '#3BB77E',
  },
  {
    title: 'Make your Breakfast Healthy and Easy',
    bgColor: '#F3E8E8',
    image: yogurtImg,
    buttonColor: '#3BB77E',
  },
  {
    title: 'The best Organic Products Online',
    bgColor: '#E7EAF3',
    image: vegetableImg,
    buttonColor: '#FDC040',
  },
]
</script>

<template>
  <main class="container">
    <section class="categories-section">
      <CategoryCard
        v-for="(category, index) in categories"
        :key="index"
        :title="category.title"
        :items="category.items"
        :image="category.image"
        :bg-color="category.bgColor"
      />
    </section>

    <section class="promotions-section">
      <PromotionCard
        v-for="(promo, index) in promotions"
        :key="index"
        :title="promo.title"
        :image="promo.image"
        :bg-color="promo.bgColor"
        :button-color="promo.buttonColor"
      />
    </section>
  </main>
</template>

<style scoped>
.container {
  max-width: 1600px;
  margin: 0 auto;
  padding: 20px;
  font-family: 'Quicksand', sans-serif;
}

.categories-section {
  display: flex;
  flex-wrap: wrap;
  gap: 15px;
  justify-content: center;
  margin-bottom: 40px;
}

.promotions-section {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 30px;
}
</style>
