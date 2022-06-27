<template>
  <div id="app">
    <TheHeader/>
    <main class="overflow-auto">
      <div class="container py-5">
        <!-- si ascolta l'evento $emit albumGenres fatto in AlbumList.vue
        al cui interno ha il genreList definitivo  -->
        <AlbumList @albumGenres="onAlbumGenre"></AlbumList>
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
  },
  methods: {
    // riceve la lista dei generi lanciati con l'$emit
    onAlbumGenre(genreList) {
      console.log("Lista generi: ", genreList)
    }
  }
}
</script>

<style lang="scss">

@import "assets/scss/main.scss";

</style>
