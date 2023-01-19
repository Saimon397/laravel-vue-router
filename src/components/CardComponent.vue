<template>
    <div class="my-card">
        <div class="img-box">
            <img :src="`${store.imageBasePath}${project.cover_image}`" alt="">
        </div>
        <div class="fw-bold fs-4 py-2">Nome: {{ project.name }}</div>
        <div class="fs-5">Tipo: {{ project.type.workflow }}</div>
        <div class="fs-5 py-2">Difficoltà: {{ project.diff_lvl }}</div>
        <router-link :to="{ name: 'single-project', params: { slug: project.slug } }" class="btn btn-primary">Vedi il
            progetto</router-link>
    </div>
</template>

<script>
import { store } from '../store';
export default {
    name: 'CardComponent',
    data() {
        return {
            store
        }
    },
    props: { project: Object }
}
</script>

<style lang="scss" scoped>
.my-card {
    width: calc(100% / 4 - 20px);
    padding: 20px 10px;
    margin: 20px 10px;
    background-color: white;

    .img-box {
        height: 180px;
        overflow: hidden;

        img {
            height: 100%;
            width: 100%;
        }
    }
}
</style>