<template>
  <div id="app">
    <TheHeader/>
    <main>
      <div class="container py-5">
        <AlbumList/>
      </div>
    </main>
  </div>
</template>

<script>
import TheHeader from './components/TheHeader.vue';
import AlbumList from './components/AlbumList.vue';


export default {
  name: 'App',
  components: {
    TheHeader,
    AlbumList
}
}
</script>

<style lang="scss">

@import "assets/scss/main.scss";

</style>
