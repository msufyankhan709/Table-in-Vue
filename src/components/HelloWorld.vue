<template>
  <v-row class="text-center">
    <v-col cols="12">
      <v-img
        :src="require('../assets/logo.svg')"
        class="my-3"
        contain
        height="200"
      />
    </v-col>

    <v-col class="mb-4">
      <h1 class="display-2 font-weight-bold mb-3">
        Welcome to Vuetify
      </h1>
      <ul v-for="todo in Todos" :key="todo.id">
        <li>{{ todo }}</li>
      </ul>
    </v-col>
  </v-row>
</template>

<script>
import axios from "axios";
import Vue from "vue";
Vue.use(axios);

export default {
  name: "HelloWorld",

  mounted() {
    axios.get("https://jsonplaceholder.typicode.com/users").then((res) => {
      this.Todos.push(res.data);
    });
  },

  data() {
    return {
      Todos: [],
    };
  },
};
</script>
