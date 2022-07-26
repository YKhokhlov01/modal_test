<template>

  <button id="show-modal" @click="isActive1 = !isActive1">Показать модальное окно</button>
  <!--Для плавности-->
  <transition name="modal">
    <!--Модальный компонент-->
    <ModalWindow v-if="isActive1" @close="isActive1 = !isActive1">
      <template v-slot:footer>
        <h3>{{ text2 }}</h3>
      </template>
    </ModalWindow>
  </transition>
</template>

<script>

import ModalWindow from './components/Modal.vue'

export default {
  name: 'App',
  components: {
    ModalWindow
  },
  data() {
    return {
      isActive1: false,
      text1: 'Показать модальное окно',
      text2: 'Выполнение тестового задания по модальному окну на vue3'
    }
  }
}
</script>

<style>
#app {
  text-align: center;
  margin-top: 60px;
}

/* Код для плавности окна */
.modal-enter-active,
.modal-leave-active {
  transition: opacity 0.8s ease;
}

.modal-enter-from,
.modal-leave-to {
  opacity: 0;
}
</style>
