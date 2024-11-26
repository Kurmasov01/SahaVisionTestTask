<template>
    <div class="modal-wrapper" @click.self="$emit('close')">
        <div class="modal">
            <h1 class="modal-title">
                {{ title }}
            </h1>
            <div class="modal-tree">
                <div class="folders-wrapper">
                    <FolderTree :folders="folders" :selectedId="selectedFolderId" @select="selectFolder" />
                </div>
            </div>
            <div class="btns-wrapper">
                <button class="btn select-btn" @click="confirm">Ок</button>
                <button class="btn select-btn" @click="$emit('close')">Закрыть</button>
            </div>
        </div>
    </div>
</template>
<script lang="ts" setup>
import { PropType, ref } from 'vue';
import FolderTree from './FolderTree.vue';

const emit = defineEmits(['close', 'select']);
const selectedFolderId = ref<number | null>(null);

defineProps({
    title: String,
    folders: {
        type: Array as PropType<Folder[]>,
        required: true,
    },
});

interface Folder {
    name: string;
    id: number;
    children: Folder[];
}

function selectFolder(id: number) {
    selectedFolderId.value = id;
}
function confirm() {
    emit('close');
    emit('select', selectedFolderId.value);
}
</script>

<style>
.modal-wrapper {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgb(120, 120, 120, 0.8);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
}

.modal {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 50%;
    background-color: white;
    border-radius: 10px;
}

.modal-tree {
    width: 100%;
}

.folder {
    display: flex;
    flex-direction: column;
    list-style: none;
    justify-content: center;
}

.btns-wrapper {
    width: 20%;
    display: flex;
    justify-content: space-between;
    margin-bottom: 20px;
}
</style>
