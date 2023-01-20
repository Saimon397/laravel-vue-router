<template>
  <header>
    <nav class="navbar navbar-expand-lg bg-body-tertiary">
      <div class="container-fluid">
        <img class="my-logo" src="../../public/img/logoboolfolio.png" alt="">
        <a class="navbar-brand fs-2 fw-bold color-brand me-5" href="#">BoolFolio</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent"
          aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item hover-underline-animation" v-for="(item, index) in NavItems" :key="index">
              <router-link :to="{ name: item.routeName }" active-class="active" class="nav-link">
                {{ item.label }}
              </router-link>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  name: 'AppHeader',
  data() {
    return {
      NavItems: [
        {
          label: 'Home',
          routeName: 'home'
        },
        {
          label: 'Projects',
          routeName: 'projects'
        },
        {
          label: 'Chi Siamo',
          routeName: 'about'
        },
        {
          label: 'Contatti',
          routeName: 'contact'
        }
      ]
    }
  }

}
</script>

<style lang="scss" scoped>
header {
  background-color: rgb(255, 255, 255);
  border-bottom: 2px solid rgb(216, 210, 210);
}

.my-logo {
  width: 100px;
}

.color-brand {
  color: rgb(248, 94, 11);
}

.hover-underline-animation {
  display: inline-block;
  position: relative;
  cursor: pointer;
}

.hover-underline-animation:after {
  content: '';
  position: absolute;
  width: 100%;
  transform: scaleX(0);
  height: 2px;
  bottom: 5px;
  left: 0;
  background-color: rgb(255, 167, 0);
  transform-origin: bottom right;
  transition: transform 0.25s ease-out;
}

.hover-underline-animation:hover:after {
  transform: scaleX(1);
  transform-origin: bottom left;
}
</style>
