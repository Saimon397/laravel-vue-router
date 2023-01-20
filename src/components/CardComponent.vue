<template>
    <div class="my-card mt-5">
        <div class="img-box">
            <img :src="`${store.imageBasePath}${project.cover_image}`" alt="">
        </div>
        <div class="fw-bold fs-4 py-2">Nome: {{ project.name }}</div>
        <div class="fs-5">Tipo: {{ project.type.workflow }}</div>
        <div class="fs-5 py-2">Difficoltà: {{ project.diff_lvl }}</div>
        <router-link :to="{ name: 'single-project', params: { slug: project.slug } }"
            class="btn color-btn d-flex justify-content-center p-2 mt-2">Vedi
            il
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
    width: 100% -10px;
    padding: 30px 20px;
    margin: 20px 10px;
    background-color: white;
    border-radius: 10px;
    box-shadow: 3px 1px 1px 1px rgb(230, 227, 227);

    .img-box {
        height: 180px;
        overflow: hidden;

        img {
            height: 100%;
            width: 100%;
            border-radius: 10px;
        }
    }
}

.color-btn {
    color: white;
    background-color: rgb(248, 94, 11);

    &:hover {
        color: white;
        background-color: rgb(202, 79, 13);
    }
}
</style>