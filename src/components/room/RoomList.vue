<template>
    <!-- room lists -->
    <div v-for="(room) in rooms" :key="room.id">
        <img class="room-img" :src="room.image" />
        <h4 @click="fnOpenModal(room)">{{ room.title }}</h4>
        <p>{{ room.price}}원</p>
    </div>
</template>
rrt
<script>
export default {
    name : 'RoomList',
    props : {
        rooms : Array,
        fnOpenModal : Function
    }
}
</script>

<style>

</style>