<template>
    <div class="blur">
        <img src="/src/assets/ghost-blurred-image.jpeg" contain class="img"/>
    </div>
</template>

<style scoped lang="scss">
$blur-size: 8px;

.blur {
    border-radius : 8px;
    overflow: hidden;
    height: max-content;
}

.img {
    filter: blur($blur-size);
    object-fit: fill;
    width: 100%;
    height: auto;
}
</style>