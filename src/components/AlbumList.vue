<template>
    <div class="row row-cols-5 g-3">
        <div class="col" v-for="album in filteredAlbums" :key="album.author">
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
    props: {
        searchedGenre: String,
        searchedAuthor: String,
    },

    data() {
        return {
            apiUrl: "https://flynn.boolean.careers/exercises/api/array/music",

            /**
             * @type { {poster: string, title: string, author: string, genre: string, year: string,}[] }
             */
            allAlbumList: [],
        };
    },

    computed: {
        filteredAlbums() {
            if(!this.searchedGenre) {
                return this.allAlbumList;
            }
            return this.allAlbumList.filter((album) => {
                return album.genre === this.searchedGenre
            })
        },
        filteredAuthors() {
            if(!this.searchedAuthors) {
                return this.allAlbumList;
            }
            return this.allAlbumList.filter((album) => {
                return album.author === this.searchedAuthor
            })
        }
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
                this.$emit("albumAuthors", this.authorList())
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
        },
        authorList() {
            const list = [];
            this.allAlbumList.forEach(album => {
                if(!list.includes(album.author)) {
                    list.push(album.author)
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