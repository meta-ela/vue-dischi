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

            /**
             * @type { {poster: string, title: string, author: string, genre: string, year: string,}[] }
             */
            allAlbumList: [],
        };
    },

    methods: {
        fetchAlbumList() {
            axios
            .get(this.apiUrl)
            .then((resp) => {
                this.allAlbumList = resp.data.response;
                // emit al padre App.vue
                // all'$emit albumGenres si fa passare la lista genreList
                this.$emit("albumGenres", this.genreList())
            })
            .catch(() => {
                alert("L'operazione non è andata a buon fine. Errore Sistema.")
            });
        },
        genreList() {
            const list = [];

            this.allAlbumList.forEach(album => {
                if(!list.includes(album.genre)) {
                    list.push(album.genre)
                }
            })

            return list
        }
    },

    mounted() {
        this.fetchAlbumList()
    },
};
</script>