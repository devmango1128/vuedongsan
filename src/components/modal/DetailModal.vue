<template>
    <!-- Modal -->
    <div class="black-bg modal" v-if="modalOpen">
        <div class="white-bg">
            <h4>{{ refRoom.title }}</h4>
            <img class="modal-room-img" :src="refRoom.image" />
            <p>{{ refRoom.content }}</p>
            <input type="number" v-model="month" :value="1"> 개월
            <br/><br/>
            <strong>{{ refRoom.price * month}}원</strong>
            <br /><br />
            <button @click="fnCloseModal">확인</button>
        </div>
    </div>
</template>

<script>
import { ref } from 'vue'

export default {
    name : 'DetailModal',
    props : {
        refRoom : Object,
        modalOpen : Boolean,
        fnCloseModal : Function
    },
    data() {
        const month = ref(1)

        return {
            month
        }
    }
}
</script>

<style>

</style>