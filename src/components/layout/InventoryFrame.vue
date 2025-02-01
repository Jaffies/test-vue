<script setup lang="ts">
    import BottomGhostContainer from "./BottomGhostContainer.vue"

    import LeftGhostContainer from "./LeftGhostContainer.vue"
    import InventoryContainer from "./InventoryContainer.vue"
</script>

<template>
    <div class="frame-background">
        <!-- <div class="vertical-flex">
            <div class="horizontal-flex">
                <LeftGhostContainer />
                <InventoryContainer />
            </div>

            <BottomGhostContainer />
        </div> -->

        <div class="grid">
            <LeftGhostContainer />
            <InventoryContainer />
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

    .vertical-flex {
        display: flex;
        flex-direction: column;
        width: min-content;
        gap: 24px;
    }

    .horizontal-flex {
        display: flex;
        gap: 24px;
        width: max-content;
    }
</style>