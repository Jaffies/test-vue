<script setup lang="ts">
import { computed, ref, useTemplateRef } from 'vue';
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
    if (!props.item) return
    dragged.value = true



    event.dataTransfer.setDragImage(dragHTML.value, -dragHTML.value.clientWidth / 2, 0)
    event.dataTransfer.setData('id', props.item.id.toString() )
    event.dataTransfer.dropEffect = 'move'
    event.dataTransfer.effectAllowed = 'move'
}

function dragEnd() {
    dragged.value = false
}

const emit = defineEmits<{
    (e : 'click') : void,
    (e : 'dropped', draggedItemId : number, item : Item) : void
}>()

function onDrop(event : DragEvent) {
    if (!event.dataTransfer) return
    if (!props.item) return

    const itemId = Number(event.dataTransfer.getData('id'))

    if (itemId == null) return

    emit('dropped', itemId, props.item)
}

const visible = computed( () => "visibility :" + dragged.value ? 'hidden' : 'visible' )
</script>

<template>
    <div :style="visible" v-if="props.item?.color" @drop="onDrop" @dragenter.prevent @dragover.prevent @click="emit('click')" class="background item-flex">
        
        <a href="" class="link" draggable="true" @dragstart="dragStart" @dragend="dragEnd" @click.prevent :key="props.item.id">
            <ItemPreview :item="props.item"/>
            <div v-show="!dragged" v-if="props.item?.count? props.item?.count > 1 : false" class="count">{{ props.item.count }}</div>
        </a>
    </div>
    <div style="visible" @click="emit('click')" @drop="onDrop" @dragenter.prevent @dragover.prevent v-else class="background"></div>
    <div v-show='dragged' ref='dragHTML' class="dragged-background">
        <ItemPreview v-if="dragged" :item="props.item"></ItemPreview>
    </div>
</template>

<style lang="scss" scoped>
.background {
    position : relative;
    border-radius: 0;
    overflow: hidden;

    &:hover {
        background-color: $background-color-hover;
    }
}

.dragged-background {
    position: absolute;
    left: 0;
    top: 0;
    transform: translate(100%, -100%);
    background-color: $background-color;

    border: 1px solid $border-color;
    border-radius: 24px;

    padding: 16px;

    display:inline-flex;
    justify-content: center;
    align-items: center;
}

.item-flex {
    display: flex;
    justify-content: center;
    align-items: center;
}

.link {
    color : inherit;
    text-decoration: inherit;

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