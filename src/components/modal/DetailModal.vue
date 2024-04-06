<template>
    <!-- Modal -->
    <div class="black-bg modal" v-if="modalOpen">
        <div class="white-bg">
            <h4>{{ refRoom.title }}</h4>
            <img class="modal-room-img" :src="refRoom.image" />
            <p>{{ refRoom.content }}</p>
            <strong>{{ refRoom.price }}원</strong>
            <br /><br />
            <button @click="fnCloseModal">확인</button>
        </div>
    </div>
</template>

<script>
export default {
    name : 'DetailModal',
    props : {
        refRoom : Object,
        modalOpen : Boolean,
        fnCloseModal : Function
    }
}
</script>

<style>

</style>