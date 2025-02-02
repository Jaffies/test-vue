<script setup lang="ts"></script>

<template>
    <a href="" @click.prevent="$emit('exit')">
        <img src="/src/assets/close-button.svg" class="close-button" />
    </a>
        
</template>

<style lang="scss" scoped>
    @use "/settings.scss" as *;
    .close-button {
        position: absolute;
        right: 8px;
        top: 8px;
        width: 14px;
        height: 14px;

        filter: if($light, invert(100%), none);
    }
</style>