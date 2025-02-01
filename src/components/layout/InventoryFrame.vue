<script setup lang="ts">
    import LeftGhostContainer from "./LeftGhostContainer.vue"
    import InventoryContainer from "./InventoryContainer.vue"
</script>

<template>
    <div class="frame-background">
        <div class="vertical-flex">
            <div class="horizontal-flex">
                <LeftGhostContainer />
                <InventoryContainer />
            </div>
            <BottomGhostContainer />
            <!-- <LeftGhostContainer />
            <InventoryContainer /> -->
        </div>
    </div>
</template>

<style lang="scss" scoped>
    .frame-background {
        display: flex;
        padding: 32px;
        width: fit-content;
        height: fit-content;
        background-color: $background-frame-color;
    }

    .vertical-flex {
        display: flex;
        flex-direction: column;
        gap: 24px;
        width: 100%
    }

    .horizontal-flex {
        display: flex;
        gap: 24px;
    }
</style>