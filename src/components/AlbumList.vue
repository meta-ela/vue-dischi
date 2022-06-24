<template>
    <div class="row row-cols-5">
        <div class="col">
            <AlbumCard/>
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
                // API ha la risposta in "response"
                this.allAlbumList = resp.data.response;
            });
        },
    },

    mounted() {
        this.fetchAlbumList()
    },

};
</script>