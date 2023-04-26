<template>
  <nav class="navbar navbar-expand-lg bg-body-tertiary">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">Nпрактика</a>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <nuxt-link exact active-class="active" class="nav-link" to="/"
              >Главная</nuxt-link
            >
          </li>
          <li class="nav-item">
            <nuxt-link active-class="active" class="nav-link" to="/users"
              >Пользователи</nuxt-link
            >
          </li>
        </ul>
        <nuxt-link class="nav-link d-flex" to="/login" v-if="!hasToken"
          >Войти</nuxt-link
        >
        <a @click.prevent="logout" class="nav-link d-flex" href="#" v-else
          >Выйти</a
        >
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  computed: {
    hasToken() {
      return this.$store.getters.hasToken;
    },
  },
  methods: {
    logout() {
      this.$store.dispatch("logout");
      this.$router.push("/login");
    },
  },
};
</script>
