<script setup lang="ts">
import Skeleton from '../ui/Skeleton.vue';

import {defineAsyncComponent} from 'vue'

const Image = defineAsyncComponent(() =>
  import('../ui/Image.vue')
)
</script>

<template>
    <div class="background">
        <Image style="min-width: 200px;"/>
    
        <p class="skeleton">
            <Skeleton>
                Lorem ipsum dolor sit amet
                Тут типо текст какой-то<br>
                Скелетончик типа круто
            </Skeleton>
        </p>

    </div>
</template>

<style scoped lang="scss">
.background {
    padding: 18px 14px 24px 14px;
    width: min-content;
}

.skeleton {
    font-size: 20px;
}
</style>