<template>
    <!-- Modal -->
    <div class="black-bg modal" v-if="modalOpen">
        <div class="white-bg">
            <h4>{{ refRoom.title }}</h4>
            <img class="modal-room-img" :src="refRoom.image" />
            <p>{{ refRoom.content }}</p>
            <input type="text" v-model="month"> 개월
            <br/><br/>
            <strong>{{ refRoom.price * month}}원</strong>
            <br /><br />
            <button @click="fnCloseModal">확인</button>
        </div>
    </div>
</template>

<script>
import { ref, watch } from 'vue'

export default {
    name : 'DetailModal',
    props : {
        refRoom : Object,
        modalOpen : Boolean,
        fnCloseModal : Function
    },
    setup() {
        
        const month = ref(1)
        
        watch(month, (newVal, oldVal) => {

            //입력한 값이 한글인 경우
            const regex = /[ㄱ-ㅎㅏ-ㅣ가-힣a-zA-Z]/

            if (regex.test(newVal)) {
                month.value = oldVal
            }
        }) 

        return {
            month,
        }
    }
}
</script>

<style>

</style>