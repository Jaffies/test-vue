<script setup lang="ts">
import BottomGhostContainer from "./BottomGhostContainer.vue"
import LeftGhostContainer from "./LeftGhostContainer.vue"
import InventoryGrid from './InventoryGrid.vue'
</script>

<template>
    <div class="frame-background">
        <div class="grid">
            <LeftGhostContainer />
            <InventoryGrid />
            <BottomGhostContainer />
        </div>
        
    </div>
</template>

<style lang="scss" scoped>
    .frame-background {
        padding: 32px;
        height: fit-content;
        background-color: $background-frame-color;
    }

    .grid {
        display: grid;
        gap: 24px;
        grid-template-columns: min-content 1fr;
        grid-template-rows: min-content max-content;
    }
</style>