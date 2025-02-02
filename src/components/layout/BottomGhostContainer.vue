<script setup lang="ts">
import CloseButton from '../ui/CloseButton.vue';
import Skeleton from '../ui/Skeleton.vue';
</script>

<template>
    <div class="background">
        <div class="flex">
            <Skeleton>
                Lorem ipsum dolor sit amet don don dooooon Test
            </Skeleton>
        </div>

        <CloseButton />
    </div>
</template>

<style lang="scss" scoped>
.background {
    position: relative;
    max-width: 100%;
    padding: 18px 63px 18px 18px;
    grid-column: span 2;
}

.flex {
    width: 100% !important;
}
</style>