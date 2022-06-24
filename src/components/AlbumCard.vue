<template>
    <div class="card">
        <div class="box_img">
            <img class="w-100" :src="album.poster" :alt="`Album di ${album.author}`">
        </div>
        <h4 class="text-white fw-bold text-uppercase">{{ album.title }}</h4>
        <div>
            <h6>{{ album.author }}</h6>
            <h6>{{ album.year }}</h6>
        </div>
    </div>
</template>

<script>
/* 
la chiamata contiene:
response: {
    poster: String,
    title: String,
    author: String,
    genre: String,
    year: String,
}
*/
export default  {
    name: "AlbumCard",
    props: {
        album: Object
    },
}

</script>


<style lang="scss" scoped>

@import "../assets/scss/_variables.scss";
.card {
    height: 100%;
    background-color: $darkblue;
    padding: 1rem;
    border-radius: 0;
}

h6 {
    color: $grey;
}
</style>