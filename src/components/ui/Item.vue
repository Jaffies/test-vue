<script setup lang="ts">
import { ref, useTemplateRef } from 'vue';
import type {Item} from '../../types/Item';
import ItemPreview from './ItemPreview.vue';
const props = defineProps<{
    item? : Item
}>()

const dragHTML = useTemplateRef('dragHTML')
const dragged = ref<boolean>(false)
function dragStart(event : DragEvent) {
    if (!dragHTML.value) return
    if (!event.dataTransfer) return
    dragged.value = true

    event.dataTransfer.setDragImage(dragHTML.value, 0, 0)
    event.dataTransfer.dropEffect = 'move'
    event.dataTransfer.effectAllowed = 'move'
    
}

function dragEnd() {
    dragged.value = false
}

defineEmits(['click'])


</script>

<template>
    <div v-show='!dragged' v-if="props.item?.color" draggable="true" @click="$emit('click')" @dragstart="dragStart" @dragend="dragEnd" class="background item-flex">
        
        <a href="" class="link" @click.prevent :key="props.item.id">
            <ItemPreview :item="props.item"/>
            <div v-show="!dragged" v-if="props.item?.count? props.item?.count > 1 : false" class="count">{{ props.item.count }}</div>
        </a>
    </div>
    <div drag-not-allowed v-else class="background"></div>
    <div v-show='dragged' ref='dragHTML' class="dragged-background">
        <ItemPreview v-if="dragged" :item="props.item"></ItemPreview>
    </div>
</template>

<style lang="scss" scoped>
    .background {
        position: relative;
        border-radius: 0;
        overflow: hidden;

        &:hover {
            background-color: $background-color-hover;
        }
    }

    .dragged-background {
        left: 0;
        top: 0;
        transform: translate(-100%, -100%);
        background-color: $background-color;

        border: 1px solid $border-color;
        border-radius: 24px;

        display:inline-flex;
        justify-content: center;
        align-items: center;
    }

    .zhopa {
        background-color :red;
    }

    .item-flex {
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .link {
        color : inherit;
        text-decoration: inherit;
        pointer-events: none;

    }   
    
    .count {
        position: absolute;
        border-radius: 8px;

        width: 32px;
        height: 32px;

        bottom: 0px;
        right: 0px;

        font-size: 10px;

        padding: 4px 4px;
        background-color: $background-color;

        transform: translate(50%, 50%);

        outline: 1px solid $border-color;
    }
</style>