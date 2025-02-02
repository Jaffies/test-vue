<script setup lang="ts">
import { ref } from 'vue';
import InfoModal from './InfoModal.vue';
import type {Item} from '../../types/Item';
import ItemComponent from '../ui/Item.vue';
import { Container } from "vue-dndrop";

const item = ref<Item|undefined>()

const items = ref<Array<Item>>( Array.from(Array(25).keys(), (x) => ({id : x, w : 1, x : x % 5, y : Math.floor(x / 5)})))

items.value[5].color = 'aqua'
items.value[5].count = 5

function deleteItem(itemId : number, count : number) {
    const item = items.value[itemId]

    if (!item.count) {
        return
    }

    if (count > item.count) {
        item.count -= count
        return
    }

    delete items.value[itemId]
}

function setItem(element : Item) {
    if (!element.count) {
        item.value = undefined
        return
    }

    item.value = element
}

</script>

<template>
    <div class="background background-grid">              
        <ItemComponent @click="setItem(element)" v-for="element in items" :item="element" :key="element.id"/>
        <InfoModal :item @exit="item = undefined" :delete="deleteItem"/>
    </div>
</template>

<style lang="scss" scoped>
    .background-grid {
        position: relative;
        display: grid;
        grid-template-rows: repeat(5, 1fr);
        grid-template-columns: repeat(5, 96px);
        grid-auto-flow: column;
        overflow: hidden;
    }

    .cell {
        border-radius: 0;
    }
</style>