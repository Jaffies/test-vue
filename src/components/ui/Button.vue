<script setup lang="ts">
    const props = defineProps<{
        closing? : boolean
    }>()

</script>

<template>
    <button :class="props.closing ? 'close-button' : 'button'">
        <a href="" @click.prevent class="link">
          <slot></slot>
        </a>
    </button>
</template>

<style lang="scss" scoped>
.button {
    color : black;
    border: none;
    outline: none;

    box-shadow: $accent-color 0 0 8px;

    border-radius: 8px;
    background-color: white;

    padding: 8px;

    &:active {
        filter : brightness(150%);
    }
}

.link {
    color : inherit;
    text-decoration: inherit;
}

.close-button {
    @extend .button;

    background-color: $accent-color;
    color: white;
}
</style>