<script lang="ts">
</script>

<template>
    <div class="background">
        <div class="">
            <span>asdf</span>
            <span>asdfasdf</span>
            <!-- <LeftGhostContainer />
            <InventoryContainer /> -->
        </div>

        <BottomGhostContainer />
    </div>
</template>

<style scoped lang="scss">
    .background {
        display: flex;
        padding: 32px;
        width: 640px;
        height: 480px;
        background-color: $background-frame-color;
    }

    .flex {
        display: flex;
        flex-direction: column;
        gap: 24px;
        width: 100%
    }
</style>