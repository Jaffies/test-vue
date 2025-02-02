<script setup lang="ts">
const emit = defineEmits<{
    (e: 'exit') : void
}>()
</script>

<template>
    <a href="" @click.prevent="emit('exit')">
        <img src="/src/assets/close-button.svg" class="close-button" />
    </a>
</template>

<style lang="scss" scoped>
.close-button {
    position: absolute;
    right: 8px;
    top: 8px;
    width: 14px;
    height: 14px;
}

@media (prefers-color-scheme: light) {
    .close-button {
        filter : invert(100%)
    }
}
</style>