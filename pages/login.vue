<template>
  <section>
    <form @submit.prevent="onSubmit">
      <h1>Страница входа</h1>
      <div class="form-group">
        <input type="text" class="form-control" />
      </div>
      <p>
        <nuxt-link to="/">На главную</nuxt-link>
      </p>
      <button class="btn btn-primary" type="submit">Логин</button>
    </form>
  </section>
</template>

<script>
export default {
  layout: "empty",
  methods: {
    onSubmit() {
      this.$store.dispatch("login");
      this.$router.push("/");
    },
  },
};
</script>

<style scoped>
form {
  width: 500px;
  margin: 0 auto;
}
</style>
