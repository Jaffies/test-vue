<script setup lang="ts">
import { ref, watch } from 'vue';
import CloseButton from '../ui/CloseButton.vue';
import Skeleton from '../ui/Skeleton.vue';
import DeleteForm from '../ui/DeleteForm.vue';
import Button from '../ui/Button.vue';
import type {Item} from '../../types/Item';
import ItemPreview from '../ui/ItemPreview.vue';

const props = defineProps<{
    item? : Item
}>()

const deleteForm = ref<boolean>(false)

watch(() => props.item, () => {
    deleteForm.value = false
})

const emit = defineEmits<{
    (e: 'exit') : void,
    (e : 'delete', item : Item, count : number) : void
}>()

function deleteItem(count : number) {
    if (!props.item) return

    emit('delete', props.item, count)
}

</script>

<template>
    <Transition>
        <div v-if="props.item?.count" class="background background-flex">
            <CloseButton @exit="emit('exit')"/>
            <ItemPreview :item="props.item" />

            <div class="line"></div>

            <div class="description">
                <Skeleton>
                    Lorem ipsum dolor sit amet tin foun newman dolor sit lorem amet sit<br/>
                    Lorem ipsum dolor sit amet tin foun newman dolor sit lorem amet sit<br/>
                    Lorem ipsum dolor sit amet tin foun newman dolor sit lorem amet sit<br/>
                    Lorem ipsum dolor sit amet tin foun newman dolor sit lorem amet sit<br/>
                </Skeleton>
            </div>

            <div class="background footer">
                <DeleteForm @cancel="deleteForm = false" @approve="deleteItem" v-if="deleteForm"></DeleteForm>
                <Button closing v-else style="width : 100%;" @click="deleteForm = true">Удалить предмет</Button>
            </div>
        </div>
    </Transition>
</template>

<style scoped lang="scss">
.v-enter-active,
.v-leave-active {
    transition: transform 0.5s ease;
}

.v-enter-from,
.v-leave-to {
    transform: translateX(100%);
}

.background-flex {
    border-radius: 0;
    position: absolute;
    right: 0px;

    height: calc(100% - 45px);
    display: flex;
    flex-direction: column;

    gap: 4px;

    width: min-content;

    padding: 45px 0px 0px 0px;

    background-color: #{$background-color}77;
    backdrop-filter: blur(4px);
}

.description {
    flex: 1 1 64px;
    padding: 10px;
    overflow-y: auto;
}

.footer {
    flex-shrink: 0;
    border-radius: 0;
    padding: 20px 21px;
    transition: height;
    transition-duration: 0.1s;
}

.line {
    width: 220px;
    height: 1px;
    background-color: $border-color;
    margin: 0px 20px;
}
</style>