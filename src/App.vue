<template>
  <div id="app">
    <NoteArranger octave="4" note="c" />
    <footer>
        <a href="https://www.freepik.com/free-photos-vectors/music">
            Music vectors created by rawpixel.com - www.freepik.com
        </a>
    </footer>
  </div>
</template>

<script>
import NoteArranger from './components/NoteArranger.vue'

export default {
  name: 'app',
  components: {
    NoteArranger
  }
}
</script>

<style>
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
    }

    footer {
        width: 100%;
        position: fixed;
        bottom: 0;
    }
</style>
