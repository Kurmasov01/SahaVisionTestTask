<template>
  <div class="main">
    <OpenBtn @openModal="openModal" />
    <Modal v-if="showModal" @close="closeModal" :title="'Выберите папку'" :folders="mockFolders" @select="showSelect" />
    <div v-if="selectedFolder">id выбранной папки: {{ selectedFolder }}</div>
  </div>
</template>


<script lang="ts" setup>
import { ref } from 'vue';
import OpenBtn from './components/OpenBtn.vue';
import Modal from './components/Modal.vue';

const showModal = ref(false);
const selectedFolder = ref<string>()

const openModal = () => {
  showModal.value = true;
};
const closeModal = () => {
  showModal.value = false;
};
const showSelect = (data: string) => {
  selectedFolder.value = data;
}


const mockFolders = [
  {
    id: 1, name: 'Папка 1', children: [
      { id: 2, name: 'Папка 1.1', children: [] },
      {
        id: 3, name: 'Папка 1.2', children: [
          { id: 4, name: 'Папка 1.2.1', children: [] }
        ]
      }
    ]
  },
  { id: 5, name: 'Папка 2', children: [] },
];
</script>

<style>
body {
  margin: 0;
  padding: 0;
}

button,
.main {
  font-family: 'Jost', sans-serif;
  font-size: 18px;
  font-weight: 500;
  font-style: normal;
}

button {
  cursor: pointer;
}

.main {
  background-color: #cecece;
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
