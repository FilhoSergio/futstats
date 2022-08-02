<template>
    <div class="section-clubes">
        <h1>Clubes Série A 2022</h1>
        <hr />
        <div style="display: flex; max-width:600px;">
            <p class="escudo" v-for="clube in clubes" :key="clube.id">
                <img :src="clube.escudos.g" />
            </p>
        </div>
    </div>
</template>

<script>
import axios from "axios";

export default {
    data: () => ({
        clubes: [],
    }),
    created() {
        this.getAll("http://localhost:3000/clubes");
    },
    mounted: function () { },
    methods: {
        getAll: function (api) {
            axios
                .get(api)
                .then((response) => {
                    console.log("dsdas", response);
                    this.clubes = response.data;
                })
                .catch((error) => {
                    console.log(error);
                });
        },
    },
};
</script>

<style>
.escudo {

    cursor: pointer;
    padding: 1.8rem;
    transition: transform .2s;
    /* Animation */

}

.escudo :hover {
    transform: scale(1.2);
}

.section-clubes {
    text-align: center;
    margin: 0 auto;
}
</style>
