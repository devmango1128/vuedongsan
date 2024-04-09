<template>
    <div class="discount">
        <h4>오늘 23시 59분까지 중개수수료 20% 할인!!</h4>
        <h5>남은 시간 : {{ countdown }}</h5>
    </div>
</template>

<script>
import { ref, computed, onMounted } from 'vue';

export default {
    name: 'TopBanner',
    setup() {
        const deadline = ref(new Date());
        deadline.value.setHours(23, 59, 59, 0); // Set deadline to today 23:59:59

        // Calculate remaining time
        const timeDifference = computed(() => {
            const currentTime = new Date();
            return deadline.value - currentTime;
        });

        // Calculate countdown
        const countdown = computed(() => {
            const hours = Math.floor(timeDifference.value / (1000 * 60 * 60));
            const minutes = Math.floor((timeDifference.value % (1000 * 60 * 60)) / (1000 * 60));
            const seconds = Math.floor((timeDifference.value % (1000 * 60)) / 1000);
            return `${hours}시간 ${minutes}분 ${seconds}초`;
        });

        // Update countdown every second
        onMounted(() => {
            const timer = setInterval(() => {
                deadline.value = new Date();
                deadline.value.setHours(23, 59, 59, 0);
            }, 1000);

            // Clean up timer on component unmount
            return () => clearInterval(timer);
        });

        return { countdown };
    }
};
</script>

<style></style>
