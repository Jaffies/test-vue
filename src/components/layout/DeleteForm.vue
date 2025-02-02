<script setup lang="ts">
    import Button from '../ui/Button.vue';
    import Input from '../ui/Input.vue';
</script>

<template>
    <div class="grid">
        <Input/>
        <Button @click="$emit('cancel')">Отмена</Button>
        <Button closing @click="$emit('approve')">Подтвердить</Button>
    </div>
</template>

<style lang="scss" scoped>
    .grid {
        display: grid;
        grid-template-columns: min-content min-content;
        gap: 10px;
        justify-content: center;
    }
</style>