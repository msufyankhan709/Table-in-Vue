<template>
  <div>
    <template>
      <v-text-field v-model="user" label="Search" class="mx-4"></v-text-field>
    </template>
    <template>
      <v-card-title>Todos</v-card-title>
      <v-card-text>
        <v-data-table :headers="headers" :items="Todos" :search="user">
        </v-data-table>
      </v-card-text>
    </template>
    <template>
      <v-row justify="center">
        <v-dialog v-model="dialog" persistent max-width="600px">
          <template v-slot:activator="{ on, attrs }">
            <v-btn color="primary" dark v-bind="attrs" v-on="on">
              Open Dialog
            </v-btn>
          </template>
          <v-card>
            <v-card-title>
              <span class="text-h5">User Profile</span>
            </v-card-title>
            <v-card-text>
              <v-container>
                <v-row>
                    <v-text-field
                      label="ID"
                    ></v-text-field>&nbsp;
                    <v-text-field
                      label="User Id"
                    ></v-text-field>
                    <v-text-field
                      label="Title"
                    ></v-text-field>
                    <v-text-field label="Description"></v-text-field>
                </v-row>
              </v-container>
            </v-card-text>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn color="blue darken-1" text @click="dialog = false">
                Close
              </v-btn>
              <v-btn color="blue darken-1" text @click="dialog = true">
                Save
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
      </v-row>
    </template>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",

  mounted() {
    this.loadTodos();
  },
  methods: {
    loadTodos() {
      fetch("https://jsonplaceholder.typicode.com/todos")
        .then((response) => response.json())
        .then((json) => {
          this.Todos = json;
        });
    },
  },

  data() {
    return {
      Todos: [],
      user: "",
      headers: [
        {
          text: "User Id",
          value: "userId",
        },
        {
          text: "ID",
          value: "id",
        },
        {
          text: "Title",
          value: "title",
        },
        {
          text: "Description",
          value: "completed",
        },
      ],
    };
  },
};
</script>
