<template>
    <div class="skeleton-text">
        <slot></slot>
    </div>
</template>

<style lang="scss" scoped>
.skeleton-text {
    filter: blur(6px);
    background: linear-gradient(to right, $skeleton-first-color, $skeleton-second-color, $skeleton-third-color);
    background-clip: text;
    text-align: center;
}
</style>