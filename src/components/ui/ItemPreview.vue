<script setup lang="ts">
import type {Item} from '../../types/Item';

    const props = defineProps<{
        item? : Item
    }>()
</script>

<template>
    <div class="container">
        <div class="main" :style="'background-color : ' + props.item?.color + ';'">
            <div class="blur"></div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
$block-size: 64px;
$block-offset: 8px;

.container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: #{$block-offset + $block-size};
}

.main {
    position: relative;
    background-color: #7FAA65;

    width: $block-size;
    height: $block-size;
}

.blur {
    position: absolute;
    right: #{-$block-offset};
    top: #{-$block-offset};

    backdrop-filter: blur(4px);

    width: $block-size;
    height: $block-size;
}
</style>