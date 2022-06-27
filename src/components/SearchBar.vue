<template>
    <div class="d-flex">
        <div class="input-group">
            <select type="text" class="form-select" v-model="genre">
                <option value="">Tutti i generi</option>
                <!-- v-for per far passare la genreList  -->
                <option 
                v-for="(genre, i) in genreList"
                :key="i"
                :value="genre">{{ genre }}</option>
            </select>
            <button class="btn " @click="onSearchClick">Cerca</button>
        </div>
    </div>
</template>

<script>

export default {
    // stesso passaggio dati di TheHeader.vue per far 
    // ricevere alla SearchBar.vue la lista
    props: {
        genreList: Array,
    },

    data() {
        return {
            genre: "",
        }
    },
    // far partire $emit al contrario per raggiungere TheHeader.vue
    // TheHeader.vue a sua volta deve raggiungere App.vue
    methods: {
        onSearchClick() {
            this.$emit("searchGenre", this.genre);
        }
    }
}

</script>



<style lang="scss" scoped>

@import "../assets/scss/_variables.scss";
.btn {
    &:hover {
        border: 2px solid white;
        color: $darkblue;
        background-color: white;
    }
    &:active {
        border: 2px solid white;
        color: $darkblue;
        background-color: white;
    }
    &:focus {
        border: 2px solid white;
        color: blueviolet;
    }
    border: 2px solid white;
    color: white;
}

</style>