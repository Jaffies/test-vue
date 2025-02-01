<script setup lang="ts">
import { ref } from 'vue';
import InfoModal from './InfoModal.vue';

const show = ref<boolean>(false)
</script>

<template>
    <div class="background background-grid">
        <div v-for="_ in 25" class="background cell"></div>

        <InfoModal :active="show"/>
    </div>
</template>

<style lang="scss" scoped>
    .background-grid {
        position: relative;
        display: grid;
        grid-template-rows: repeat(5, 1fr);
        grid-template-columns: repeat(5, 96px);
        grid-auto-flow: column;
        overflow: hidden;
    }

    .cell {
        border-radius: 0;
    }
</style>