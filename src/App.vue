<template>
  <div id="app">
    <!-- inoltrare alla prop :genre-list il risultato della lista
    la prop aggiorna automaticamente le modifiche effettuate nella lista-->
    <TheHeader :genre-list="genreList" @searchGenre="onSearchGenre"></TheHeader>
    <main class="overflow-auto">
      <div class="container py-5">
        <!-- si ascolta l'evento $emit albumGenres fatto in AlbumList.vue
        al cui interno ha il genreList definitivo  -->
        <AlbumList @albumGenres="onAlbumGenre" :searched-genre="searchedGenre"></AlbumList>
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

  data() {
    return {
      // salvare localmente la lista per poterla richiamare nei figli
      // di App.vue in cui bisogna leggerlo 
      genreList: [],
      searchedGenre: "",
    };
  },

  methods: {
    // riceve la lista dei generi lanciati con l'$emit
    onAlbumGenre(genreList) {
      console.log("Lista generi: ", genreList)
      // salvare questo risultato nel genreList in data 
      this.genreList = genreList
    },
    onSearchGenre(genre) {
      this.searchedGenre = genre;
    },
  }
}
</script>

<style lang="scss">

@import "assets/scss/main.scss";

</style>
