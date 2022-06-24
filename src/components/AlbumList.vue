<template>
    <div class="row row-cols-5 g-3">
        <div class="col" v-for="album in allAlbumList" :key="album.author">
            <AlbumCard :album="album"></AlbumCard>
        </div>
    </div>
</template>

<script>
import axios from "axios";
import AlbumCard from "./AlbumCard.vue";

export default  {
    name: "AlbumList",
    components: { AlbumCard },
    data() {
        return {
            apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
            allAlbumList: [],
        };
    },

    methods: {
        fetchAlbumList() {
            axios.get(this.apiUrl).then((resp) => {
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
                this.allAlbumList = resp.data.response;
            });
        },
    },

    mounted() {
        this.fetchAlbumList()
    },

};
</script>