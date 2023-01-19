<template>
    <div class="container mt-5" v-if="project">
        <div class="row g-4">
            <div class="col-4 d-flex justify-content-center align-items-center">
                <div class="container card-box">
                    <img :src="`${store.imageBasePath}${project.cover_image}`" class="card-img-top" :alt="project.name">
                    <div>{{ project.name }}</div>
                    <div>{{ project.diff_lvl }}</div>
                    <div v-for="language in project.languages">{{ language.name }}</div>
                    <div>{{ project.framework }}</div>
                    <div>{{ project.team }}</div>
                    <div>{{ project.git_link }}</div>
                    <div>{{ project.description }}</div>
                    <div class="fw-bold">Workflow: {{ project.type.workflow }}</div>
                </div>
            </div>
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

</style>