<template>
    <div class="cards">
        <CardComponent v-for="(project, index) in projects" :key="index" :project="project"></CardComponent>
    </div>
</template>

<script>
import axios from 'axios';
import CardComponent from '../components/CardComponent.vue';
import { store } from '../store';
export default {
    data() {
        return {
            store,
            projects: [],
        };
    },
    methods: {
        getProjects() {
            axios.get(`${store.apiBaseUrl}/projects`).then((response) => {
                console.log(response.data.results.data)
                this.projects = response.data.results.data;
            });
        }
    },
    mounted() {
        this.getProjects();
    },
    components: { CardComponent }
}
</script>

<style lang="scss" scoped>

</style>