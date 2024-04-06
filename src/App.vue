<template>
  <div class="black-bg modal" v-if="modalOpen">
    <div class="white-bg">
        <h4>상세페이지</h4>
        <p>상세페이지 내용</p>
        <button @click="closeModal">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="(menu, idx) in menus" :key="idx">
      {{ menu }}
    </a>
  </div>

  <div v-for="(room) in rooms" :key="room.id">
    <img class="room-img" :src="room.image" />
    <h4 @click="modalOpen = true">{{ room.title }}</h4>
    <p>{{ room.price }}원</p>
  </div>
</template>

<script>
import rooms from '@/assets/rooms.js'


export default {
  name: 'App',
  data() {

    const closeModal = () => {
      this.modalOpen = false
    }

    return {
      modalOpen : false,
      menus : ['Home', 'Shop', 'About'],
      closeModal,
      rooms
    } 
  },
  components: {
  }
}
</script>

<style>
body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

.black-bg {
  width:100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}

.white-bg {
  width: 100%;
  background:#fff;
  border-radius: 8px;
  padding: 20px;
}


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

.room-img {
  width: 100%;
  margin-top: 40px;
}
</style>
