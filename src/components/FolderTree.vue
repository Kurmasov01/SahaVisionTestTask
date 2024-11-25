<template>
    <div class="modal-wrapper">
        <div class="modal">
            <h1 class="modal-title">
                Выбор паки
            </h1>
            <div class="modal-tree">
                <div class="folders-wrapper">
                    <ul class="folders">
                        <li class="folder">
                            <img src="@/assets/icons8-folder.svg" width="28px" alt="">
                            <span class="folder-title">Папка</span>
                        </li>
                    </ul>
                </div>

            </div>
            <div class="btns-wrapper">
                <button class="btn select-btn">
                    Ок
                </button>
                <button class="btn select-btn">
                    Закрыть
                </button>
            </div>

        </div>
    </div>
</template>
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
.modal-tree{
    width: 100%;
}
.folder {
    display: flex;
    align-items: center;
    list-style: none;
}

.btns-wrapper {
    width: 20%;
    display: flex;
    justify-content: space-between;
    margin-bottom: 20px;
}
</style>
<script lang="ts" setup>

</script>