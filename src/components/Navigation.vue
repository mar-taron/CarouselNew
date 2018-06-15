<template>
  <div>
    <b-navbar toggleable="md" type="dark" variant="success" fixed="top">
      <b-navbar-toggle target="nav_collapse"></b-navbar-toggle>
      <b-navbar-brand href="#">Vue Carousel</b-navbar-brand>
      <b-collapse is-nav id="nav_collapse">
        <b-navbar-nav class="ml-auto">
          <b-nav-item v-for="routes in links" v-bind:key="routes.id" :href="routes.page">{{ routes.text }}</b-nav-item>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
  </div>
</template>

<script>
export default {
  name: 'Navigation',
  data() {
    return {
      links: [
        {
          id: 0,
          text: 'Home',
          page:'/'
        },
        {
          id: 1,
          text: 'About',
          page:'/about'
        },
        {
          id: 2,
          text: 'Contact',
          page:'/contact'
        }
      ]
    }
  }
}
</script>
<style>
.spacing{
  margin-right: 10px;
}
</style>

