<script setup lang="ts">
    import CloseButton from '../ui/CloseButton.vue';
    import Item from '../ui/Item.vue';
    import Skeleton from '../ui/Skeleton.vue';

    const props = defineProps<{
        active? : boolean
    }>()
</script>

<template>
    <div v-if="props.active" class="background">
        <CloseButton />

        <Item />
        <div class="line">
        </div>

        <div class="description">
            <Skeleton>
                Lorem ipsum dolor sit amet tin foun newman dolor sit lorem amet sit<br/>
                Lorem ipsum dolor sit amet tin foun newman dolor sit lorem amet sit<br/>
                Lorem ipsum dolor sit amet tin foun newman dolor sit lorem amet sit<br/>
                Lorem ipsum dolor sit amet tin foun newman dolor sit lorem amet sit<br/>
            </Skeleton>
        </div>

        <div class="footer">

        </div>
    </div>
</template>

<style scoped lang="scss">
    .background {
        border-radius: 0;
        position: absolute;
        right: 0px;

        display: flex;
        flex-direction: column;

        gap: 4px;

        width: min-content;

        padding: 55px 15px 18px 15px;

        background-color: #{$background-color}77;
        backdrop-filter: blur(4px);

    }

    .description {
        flex: 1 1 64px;
    }

    .footer {
        height: 256px;
        background-color: red;
    }

    .line {
        width: 220px;
        height: 1px;
        background-color: $border-color;
    }
</style>