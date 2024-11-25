<template>

  <div class="main">
    <OpenBtn></OpenBtn>
  </div>
</template>

<style>
body {
  margin: 0;
  padding: 0;
}
button{
  font-family: 'Jost', sans-serif;
  font-size: 18px ;
  font-weight: 500 ;
  font-style: normal;
  cursor: pointer;
}
.main {
  font-family: 'Jost', sans-serif !important;
  font-size: 18px !important;
  font-weight: 500 !important;
  font-style: normal !important;
  background-color: #cecece;
  height: 100vh;
}
</style>
<script lang="ts" setup>
import OpenBtn from './components/OpenBtn.vue';
import Modal from './components/FolderTree.vue';
</script>
