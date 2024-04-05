<template>
  <div class="menu">
    <a v-for="(menu, idx) in menus" :key="idx">
      {{ menu }}
    </a>
  </div>
  <div v-for="(product) in products" :key="product.key">
    <h4>{{ product.name }}</h4>
    <p>{{ product.price }}만원</p>
    <button @click="product.count++">허위매물신고</button><span>신고수 : {{ product.count }} 건</span>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      menus : ['Home', 'Shop', 'About'],
      products : [
        {id:'_0', name: '역삼동원룸', price: 1000, count: 0},
        {id:'_1', name: '천호동원룸', price : 2000, count : 0},
        {id:'_2', name: '마포구원룸', price : 250, count: 0}
      ]
    } 
  },
  components: {
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background : #f8cb02;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: #000;
  padding: 5px;
  font-weight: 700;
}

button {
  padding: 5px;
  background:#f8cb02;
  border : 1px solid #f8cb02;
  border-radius : 3px;
  cursor: pointer;
}

span {
  display: inline-block;
  font-size: 14px;
  margin-left : 5px;
}
</style>
