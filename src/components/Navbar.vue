<template>
  <div>
    <b-navbar toggleable="lg" type="dark" variant="dark">
      <b-navbar-brand href="#">ToDo Vue</b-navbar-brand>

      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav>
            <router-link class="nav-item" to="/">Tarefas</router-link> |
            <router-link class="nav-item" to="/form">Formulario</router-link>
        </b-navbar-nav>

      </b-collapse>
    </b-navbar>
  </div>
</template>

<script>
export default {
    name: 'Navbar',
};
</script>

<style scoped>
.nav-item{
    color: #fff;
    margin: 0 0.5rem;
    text-decoration: none;
}
</style>