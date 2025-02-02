<script setup lang="ts">
import { ref } from 'vue';
import InfoModal from './InfoModal.vue';
import type {Item} from '../../types/Item';
import ItemComponent from '../ui/ItemComponent.vue'

function createItem(id : number) {
    return ({id : id})
}

const modalItem = ref<Item|undefined>()
const items = ref<Array<Item>>( Array.from(Array(25).keys(), x => createItem(x)))

items.value[5].color = 'aqua'
items.value[5].count = 5

items.value[7].color = 'green'
items.value[7].count = 10

function deleteItem(item : Item, count : number) {
    if (!item.count) {
        return
    }

    if (count < item.count) {
        item.count -= count
        modalItem.value = undefined
        return
    }

    delete item.color
    delete item.count
}

function setItem(element : Item) {
    if (!element.count) {
        modalItem.value = undefined
        return
    }

    modalItem.value = element
}

function onDrop(itemId : number, element : Item) {
    const draggedItem = items.value[itemId]

    items.value[itemId] = element
    items.value[element.id] = draggedItem

    draggedItem.id = element.id
    element.id = itemId   
}
</script>

<template>
    <div class="background background-grid">              
        <ItemComponent @dropped="onDrop" @click="setItem(element)" v-for="element in items" :item="element" :key="element.id"/>
        <InfoModal :item="modalItem" @delete="deleteItem" @exit="modalItem = undefined" :delete="deleteItem"/>
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
</style>