<template>

  <!-- 상세보기 Modal Component -->
  <DetailModal :refRoom="refRoom" :modalOpen="modalOpen" :fnCloseModal="fnCloseModal" />

  <!-- 메뉴 -->
  <div class=" menu">
    <a v-for="(menu, idx) in menus" :key="idx">
      {{ menu }}
    </a>
  </div>

  <!-- 배너 컴포넌트 -->
  <TopBanner />

  <!-- room lists -->
  <div v-for="(room) in rooms" :key="room.id">
    <img class="room-img" :src="room.image" />
    <h4 @click="fnOpenModal(room)">{{ room.title }}</h4>
    <p>{{ room.price }}원</p>
  </div>
</template>

<script>
import rooms from '@/assets/rooms.js'
import { ref } from 'vue'
import TopBanner from '@/components/banner/TopBanner.vue'
import DetailModal from '@/components/modal/DetailModal.vue'

export default {
  name: 'App',
  data() {

    const refRoom = ref({})

    //모달창 닫기
    const fnCloseModal = () => {
      this.modalOpen = false
    }
    //모달창 열기
    const fnOpenModal = (room) => {
      this.modalOpen = true
      refRoom.value = room
    }

    return {
      modalOpen : false,
      menus : ['Home', 'Shop', 'About'],
      fnCloseModal,
      fnOpenModal,
      rooms,
      refRoom
    } 
  },
  components: {
    TopBanner,
    DetailModal
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

.modal-room-img {
  width: 100%;
  margin : 10px;
}

.discount {
  background : #eee;
  padding: 5px;
  margin: 5px;
}
</style>
