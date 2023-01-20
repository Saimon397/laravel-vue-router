<template>
    <div class="d-flex justify-content-center align-items-center mt-5" v-if="project">
        <div class="my-card-single">
            <img :src="`${store.imageBasePath}${project.cover_image}`" class="card-img-top" :alt="project.name">
            <div class="my-text mt-5">Name:&ensp;{{ project.name }}</div>
            <div class="my-text">Difficulty:&ensp;{{ project.diff_lvl }}</div>
            <div class="my-text" v-for="language in project.languages">Languages:&ensp;{{ language.name }}</div>
            <div class="my-text">Framework:&ensp;{{ project.framework }}</div>
            <div class="my-text">Team:&ensp;{{ project.team }}</div>
            <div class="my-text">Link:&ensp;{{ project.git_link }}</div>
            <div class="my-text">Description:&ensp;{{ project.description }}</div>
            <div class="my-text">Workflow:&ensp;{{ project.type.workflow }}</div>
        </div>
    </div>
    <div v-else>
        <h3 class="text-center">Loading...</h3>
    </div>
</template>

<script>
import axios from 'axios';
import { store } from '../store'
export default {
    data() {
        return {
            store,
            project: null
        }
    },
    methods: {
        getPorject() {
            axios.get(`${store.apiBaseUrl}/projects/${this.$route.params.slug}`).then((response) => {
                console.log(response.data)
                if (response.data.success) {
                    console.log('sonoqui')
                    this.project = response.data.results;
                } else {
                    this.$router.push({ name: 'not-found' });
                }
            });
        }
    },
    mounted() {
        setTimeout(this.getPorject, 3000);
    }
}
</script>

<style lang="scss" scoped>
.my-card-single {
    width: 600px;
    padding: 30px 40px;
    margin: 20px 10px;
    background-color: white;
    border-radius: 10px;
    box-shadow: 3px 1px 1px 1px rgb(230, 227, 227);

    img {
        height: 100%;
        width: 100%;
        border-radius: 10px;
    }
}

.my-text {
    margin-top: 10px;
    font-size: 30px;
}
</style>