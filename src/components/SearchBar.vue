<template>
    <div class="d-flex">
        <div class="input-group">
            <select type="text" class="form-select">
                <option value="">Scegli un genere</option>
            </select>
            <button class="btn ">Cerca</button>
        </div>
    </div>
</template>

<script setup>

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