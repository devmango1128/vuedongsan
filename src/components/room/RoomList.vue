<template>
  <div class="price-div">
    <button @click="fnPriceDefault" class="price-btn">기본순</button>
    <button @click="fnPriceAsc" class="price-btn">가격순↑</button>
    <button @click="fnPriceDesc" class="price-btn">가격순↓</button>
  </div>

  <!-- room lists -->
  <div v-for="(room) in sortedRooms" :key="room.id">
    <img class="room-img" :src="room.image" />
    <h4 @click="fnOpenModal(room)">{{ room.title }}</h4>
    <p>{{ room.price}}원</p>
  </div>
</template>

<script>
import { ref, watch } from 'vue'
export default {
  name: 'RoomList',
  props: {
    rooms: Array,
    fnOpenModal: Function
  },
  setup(props) {

    const sortedRooms = ref([...props.rooms])
    const originalRooms = ref([...props.rooms])

    const fnPriceDefault = () => {
      sortedRooms.value = [...originalRooms.value]
    };

    const fnPriceAsc = () => {
      sortedRooms.value = [...props.rooms].sort((a, b) => a.price - b.price);
    };

    const fnPriceDesc = () => {
      sortedRooms.value = [...props.rooms].sort((a, b) => b.price - a.price);
    };

    watch(() => props.rooms, (newValue) => {
      sortedRooms.value = [...newValue];
    });

    return {
      fnPriceDefault,
      fnPriceAsc,
      fnPriceDesc,
      sortedRooms
    }
  }
}
</script>

<style>
</style>
