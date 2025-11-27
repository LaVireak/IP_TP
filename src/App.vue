<script>
import axios from 'axios'
import CategoryCard from './components/CategoryCard.vue'
import PromotionCard from './components/PromotionCard.vue'
import ProductCard from './components/ProductCard.vue'

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

// Product images
import mangoImg from './components/mango.png'
import cornImg from './components/corn.png'
import chilliImg from './components/chilli.png'
import lemonImg from './components/lemon.png'
import steak1Img from './components/steak1.png'
import steak2Img from './components/steak2.png'
import steak3Img from './components/steak3.png'
import steak4Img from './components/steak4.png'

export default {
  components: {
    CategoryCard,
    PromotionCard,
    ProductCard,
  },
  data() {
    return {
      categories: [],
      promotions: [],
      staticCategories: [
        { title: 'Cake & Milk', items: 14, bgColor: '#F2FCE4', image: burgerImg },
        { title: 'Peach', items: 17, bgColor: '#FFFCEB', image: peachImg },
        { title: 'Organic Kiwi', items: 21, bgColor: '#ECFFEC', image: kiwiImg },
        { title: 'Red Apple', items: 68, bgColor: '#FEEFEA', image: appleImg },
        { title: 'Snack', items: 34, bgColor: '#FFF3EB', image: snackImg },
        { title: 'Black plum', items: 25, bgColor: '#FFF3FF', image: plumImg },
        { title: 'Vegetables', items: 65, bgColor: '#F2FCE4', image: cabbageImg },
        { title: 'Headphone', items: 33, bgColor: '#FFFCEB', image: headphoneImg },
        { title: 'Cake & Milk', items: 54, bgColor: '#F2FCE4', image: cakeImg },
        { title: 'Orange', items: 63, bgColor: '#FFF3FF', image: orangeImg },
      ],
      staticPromotions: [
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
      ],
      products: [
        {
          badge: { text: '-17%', color: '#3BB77E' },
          image: mangoImg,
          category: 'Hodo Foods',
          title: 'Seeds of Change Organic Quinoa, Brown, & Red Rice',
          rating: 4.0,
          price: 2.51,
          oldPrice: 2.8,
        },
        {
          badge: { text: 'Hot', color: '#FD6E6E' },
          image: cornImg,
          category: 'Hodo Foods',
          title: 'All Natural Italian-Style Chicken Meatballs',
          rating: 4.0,
          price: 2.51,
          oldPrice: 2.8,
        },
        {
          badge: { text: 'Sale', color: '#FDC040' },
          image: orangeImg,
          category: 'Hodo Foods',
          title: "Angie's Boomchickapop Sweet & Salty Kettle Corn",
          rating: 4.0,
          price: 2.51,
          oldPrice: 2.8,
        },
        {
          badge: null,
          image: chilliImg,
          category: 'Hodo Foods',
          title: 'Foster Farms Takeout Crispy Classic Buffalo Wings',
          rating: 4.0,
          price: 2.51,
          oldPrice: 2.8,
        },
        {
          badge: null,
          image: lemonImg,
          category: 'Hodo Foods',
          title: 'Blue Diamond Almonds Lightly Salted Vegetables',
          rating: 4.0,
          price: 2.51,
          oldPrice: 2.8,
        },
        {
          badge: null,
          image: steak1Img,
          category: 'Hodo Foods',
          title: 'Chobani Complete Vanilla Greek Yogurt',
          rating: 4.0,
          price: 2.51,
          oldPrice: 2.8,
        },
        {
          badge: { text: 'Sale', color: '#FDC040' },
          image: steak2Img,
          category: 'Hodo Foods',
          title: 'Canada Dry Ginger Ale - 2 L Bottle - 200ml - 400g',
          rating: 4.0,
          price: 2.51,
          oldPrice: 2.8,
        },
        {
          badge: null,
          image: steak3Img,
          category: 'Hodo Foods',
          title: 'Encore Seafoods Stuffed Alaskan Salmon',
          rating: 4.0,
          price: 2.51,
          oldPrice: 2.8,
        },
        {
          badge: null,
          image: steak4Img,
          category: 'Hodo Foods',
          title: "Gorton's Beer Battered Fish Fillets with soft paper",
          rating: 4.0,
          price: 2.51,
          oldPrice: 2.8,
        },
        {
          badge: { text: 'Hot', color: '#FD6E6E' },
          image: plumImg, // Using plum as placeholder for ice cream if not available
          category: 'Hodo Foods',
          title: 'Haagen-Dazs Caramel Cone Ice Cream Ketchup',
          rating: 4.0,
          price: 2.51,
          oldPrice: 2.8,
        },
      ],
    }
  },
  methods: {
    getImage(imagePath, title) {
      const lowerTitle = title.toLowerCase()
      if (lowerTitle.includes('cake')) return burgerImg // "Cake & Milk" -> burger.png (based on previous code)
      if (lowerTitle.includes('peach')) return peachImg
      if (lowerTitle.includes('kiwi')) return kiwiImg
      if (lowerTitle.includes('apple')) return appleImg
      if (lowerTitle.includes('snack')) return snackImg
      if (lowerTitle.includes('plum')) return plumImg
      if (lowerTitle.includes('vegetable')) return cabbageImg // "Vegetables" -> cabbage.png
      if (lowerTitle.includes('headphone')) return headphoneImg
      if (lowerTitle.includes('orange')) return orangeImg
      if (lowerTitle.includes('onion')) return onionImg
      if (lowerTitle.includes('breakfast')) return yogurtImg // "Make your Breakfast..." -> yogurt.png
      if (lowerTitle.includes('organic products')) return vegetableImg // "The best Organic..." -> vegetable.png

      return burgerImg // Fallback
    },
    fetchCategories() {
      axios
        .get('http://localhost:3000/api/categories')
        .then((response) => {
          if (response.data && response.data.length > 0) {
            this.categories = response.data.map((item) => ({
              title: item.name,
              items: item.productCount,
              bgColor: item.color,
              image: this.getImage(item.image, item.name),
            }))
          } else {
            console.log('API returned empty categories, using fallback data')
            this.categories = this.staticCategories
          }
        })
        .catch((error) => {
          console.error('Error fetching categories, using fallback data:', error)
          this.categories = this.staticCategories
        })
    },
    fetchPromotions() {
      axios
        .get('http://localhost:3000/api/promotions')
        .then((response) => {
          if (response.data && response.data.length > 0) {
            this.promotions = response.data.map((item) => ({
              title: item.title,
              bgColor: item.color,
              image: this.getImage(item.image, item.title),
              buttonColor: item.buttonColor,
            }))
          } else {
            console.log('API returned empty promotions, using fallback data')
            this.promotions = this.staticPromotions
          }
        })
        .catch((error) => {
          console.error('Error fetching promotions, using fallback data:', error)
          this.promotions = this.staticPromotions
        })
    },
    shopNow() {
      // Placeholder
    },
  },
  mounted() {
    this.fetchCategories()
    this.fetchPromotions()
  },
}
</script>

<template>
  <main class="container">
    <div class="section-header">
      <h2 class="section-title">Featured Categories</h2>
      <div class="filters">
        <span class="active">All</span>
        <span>Milks & Dairies</span>
        <span>Coffes & Teas</span>
        <span>Pet Foods</span>
        <span>Meats</span>
        <span>Vegetables</span>
        <span>Fruits</span>
      </div>
    </div>
    <section class="categories-section">
      <div v-if="categories.length === 0" class="loading">Loading categories...</div>
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
      <div v-if="promotions.length === 0" class="loading">Loading promotions...</div>
      <PromotionCard
        v-for="(promo, index) in promotions"
        :key="index"
        :title="promo.title"
        :image="promo.image"
        :bg-color="promo.bgColor"
        :button-color="promo.buttonColor"
      />
    </section>

    <div class="section-header">
      <h2 class="section-title">Popular Products</h2>
      <div class="filters">
        <span class="active">All</span>
        <span>Milks & Dairies</span>
        <span>Coffes & Teas</span>
        <span>Pet Foods</span>
        <span>Meats</span>
        <span>Vegetables</span>
        <span>Fruits</span>
      </div>
    </div>

    <section class="products-section">
      <ProductCard
        v-for="(product, index) in products"
        :key="index"
        :badge="product.badge"
        :image="product.image"
        :category="product.category"
        :title="product.title"
        :rating="product.rating"
        :price="product.price"
        :old-price="product.oldPrice"
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
  margin-bottom: 50px;
}

.products-section {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(230px, 1fr));
  gap: 25px;
}

.section-title {
  font-size: 32px;
  font-weight: 700;
  color: #253d4e;
  margin-bottom: 30px;
  margin-top: 40px;
}

.section-title:first-of-type {
  margin-top: 0;
}

.section-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 30px;
  flex-wrap: wrap;
}

.section-header .section-title {
  margin: 0;
}

.filters {
  display: flex;
  gap: 20px;
  font-size: 16px;
  font-weight: 600;
  color: #253d4e;
}

.filters span {
  cursor: pointer;
  transition: color 0.3s;
}

.filters span:hover,
.filters span.active {
  color: #3bb77e;
}

.loading {
  width: 100%;
  text-align: center;
  padding: 20px;
  color: #7e7e7e;
}
</style>
