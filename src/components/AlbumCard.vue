<template>
    <div class="card">
        <div class="box_img">
            <img class="w-100 text-white" 
            :src="albumPoster" 
            :alt="`Album di ${album.author}`"
            :error="imageError">
            <!-- :src="album.poster"  -->
        </div>
        <h4 class="text-white fw-bold text-uppercase">{{ album.title }}</h4>
        <div class="mt-3">
            <h6>{{ album.author }}</h6>
            <h6>{{ album.year }}</h6>
        </div>
    </div>
</template>

<script>

export default  {
    name: "AlbumCard",
    props: {
        /**
         * @type { {poster: string, title: string, author: string, genre: string, year: string,} }
         */
        album: {
            type: Object,
            required: true,
        },
    },
    data() {
        return {
            albumPoster: "",
        }
    },
    methods: {
        imageError() {
            this.albumPoster = "/img/image_error.png";
        },
    },
    mounted() {
        this.albumPoster = this.album.poster;
    }
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