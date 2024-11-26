<template>
    <div class="open-btn-wrapepr">
        <button class="btn" @click="openModal">
            Открыть
        </button>
    </div>
</template>

<style>
.open-btn-wrapepr {
    display: flex;
    justify-content: center;
}

.btn {
    margin-top: 20px;
    height: 40px;
    width: 80px;
    padding: 5px;
    border-radius: 10px;
    background-color: rgb(49, 219, 52);
    border: none;
}
</style>

<script lang="ts" setup>
const emit = defineEmits(['openModal']);

const openModal = () => {
    emit('openModal');
};
</script>
