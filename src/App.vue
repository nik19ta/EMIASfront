<template>
  <Main :host='host' />
</template>

<script>
import Main from './components/Main.vue'


export default {
  name: 'App',
  components: {
    Main
  },
  data: function() {
    return {
      host: "http://localhost:3000/"
    }
  },
  mounted() {
    document.ondragstart = noselect;
    // запрет на перетаскивание
    document.onselectstart = noselect;
    // запрет на выделение элементов страницы
    // document.oncontextmenu = noselect;
    // запрет на выведение контекстного меню
    function noselect() {return true;}
  }
}
</script>

<style>
#app {
  padding: 0;
  margin: 0;
  font-family: Croc;
  /* -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale; */
  background: rgb(243,243,243);
}
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  /* font-family: CrocWebBold, CrocWebLight, CrocWebRegular;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;  */
}
</style>
