<template>
  <section>
    <h1>Страница пользователей</h1>
    <ul>
      <li v-for="user of users" :key="user.id">
        <a href="#" @click.prevent="openUser(user)"> {{ user.name }}</a>
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  middleware({ store, redirect }) {
    if (!store.getters.hasToken) {
      return redirect("/login");
    }
  },
  async asyncData({ $axios }) {
    const users = await $axios.$get(
      "https://jsonplaceholder.typicode.com/users"
    );
    return { users };
  },
  data: () => ({
    users: [],
  }),
  methods: {
    openUser(user) {
      this.$router.push("/users/" + user.id);
    },
  },
};
</script>
