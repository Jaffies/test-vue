<script setup lang="ts">
import { ref } from 'vue';
import Button from '../ui/Button.vue';

const count = ref<number>(0)

const emit = defineEmits<{
    (e : 'cancel') : void,
    (e : 'approve', count : number) : void
}>()
</script>

<template>
    <div class="grid">
        <input type="text" v-model="count" required class="main" placeholder="Введите количество"/>
        <Button @click="emit('cancel')">Отмена</Button>
        <Button closing @click="emit('approve', count)">Подтвердить</Button>
    </div>
</template>

<style lang="scss" scoped>
.grid {
    display: grid;
    grid-template-columns: min-content min-content;
    gap: 10px;
    justify-content: center;
}

.main {
    background-color: $background-color;
    outline: 1px solid $border-color;
    grid-column: span 2;
    border: none;
    border-radius: 4px;
    padding: 8px;

    &:focus {
        box-shadow: white 0 0 4px;
    }
}
</style>