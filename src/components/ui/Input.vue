<template>
    <input type="text" required class="main" placeholder="Введите количество"/>
</template>

<style lang="scss" scoped>
    .main {
        background-color: $background-color;
        outline: 1px solid $border-color;
        grid-column: span 2;
        border: none;
        border-radius: 4px;
        padding: 8px;

        &:focus {
            box-shadow: white 0 0 4px;
        }
    }
</style>