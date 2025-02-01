<template>
    <div class="background">
        <div class="blur">
            <img src="/src/assets/ghost-blurred-image.jpeg" class="img"/>
        </div>

        <p class="skeleton-text">
            Lorem ipsum dolor sit amet
            Тут типо текст какой-то<br>
            Скелетончик типа круто
        </p>
    </div>
</template>

<style scoped lang="scss">
    $blur-size: 8px;

    .background {
        padding: 18px 14px 24px 14px;
        width: min-content;
    }

    .img {
        filter: blur($blur-size)
    }

    .skeleton-text {
        filter: blur($blur-size);
        background: linear-gradient(to right, #3C3C3C, #444444, #333333);
        background-clip: text;
        text-align: center;
    }


    .blur {
        border-radius : 8px;
        overflow: hidden;
    }
</style>