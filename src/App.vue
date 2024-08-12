<template>
  <div id="app">
    <PopupWithImage :imageUrl="imageUrl" :isOpen="isShowQuest" @close="handleClosePopup">
      <template v-slot:title>
        <h1>Какой-то тайтл</h1>
      </template>
      <template v-slot:subtitle>
        <h2>Какой-то сбтайтл</h2>
      </template>
      <template v-slot:description>
        <p>Это описание</p>
      </template>
    </PopupWithImage>
    <button class="open-button" @click="handleOpenPopup">Открыть</button>
  </div>
</template>

<script>
import PopupWithImage from './components/PopupWithImage/PopupWithImage.vue';
import questionImage from '../public/questionImage.jpg';

export default {
  name: 'App',
  data() {
    return {
      imageUrl: questionImage,
      isShowQuest: false
    };
  },
  components: {
    PopupWithImage
  },
  methods: {
    handleOpenPopup() {
      this.isShowQuest =  true
    },
    handleClosePopup() {
      this.isShowQuest =  false
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  height: 100vh;
  background-color: antiquewhite;
}

.open-button {
  font-size: 20px;
  margin: 10px;
}


</style>./components/Popup/QuestPopup.vue
