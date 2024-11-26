<template>
    <ul class="folders">
        <li class="folder" v-for="(item, index) in folders" :key="index" :id="item.id.toString()">
            <div class="folder-wrapper">
                <span v-if="item.children.length > 0" @click="toggle(item.id)">
                    {{ isExpanded(item.id) ? '-' : '+' }}
                </span>
                <img src="@/assets/icons8-folder.svg" width="28px" />
                <span @click="selectFolder(item.id)" :class="{ selected: props.selectedId === item.id }"
                    class="folder-title">
                    {{ item.name }}
                </span>
            </div>
            <FolderTree v-if="isExpanded(item.id)" :folders="item.children" :selectedId="props.selectedId"
                @select="selectFolder" />
        </li>
    </ul>
</template>

<script lang="ts" setup>
import { defineProps, defineEmits, ref, PropType } from 'vue';
import type { Folder } from 'src/types/types.ts';

type FolderTreeProps = {
    selectedId: number | null,
    folders: Folder[],
}

const props = defineProps<FolderTreeProps>()
const expandedFolders = ref<Set<number>>(new Set());
const emit = defineEmits(['select']);

function toggle(id: number) {
    if (expandedFolders.value.has(id)) {
        expandedFolders.value.delete(id);
    } else {
        expandedFolders.value.add(id);
    }
}

function isExpanded(id: number): boolean {
    return expandedFolders.value.has(id);
}

function selectFolder(id: number) {
    emit('select', id);
}

</script>

<style>
.selected {
    font-weight: bold;
    color: blue;
}

.folder-wrapper {
    display: flex
}
</style>