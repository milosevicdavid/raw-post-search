<template>
  <div id="app">
    <div class="wrapper">
      <br />

      <input
        @change.prevent="submitTask"
        v-model="input"
        type="text"
        placeholder="Insert task"
        list="posts"
        name="posts"
      />
      <datalist id="posts">
        <option id="option-class" v-for="(item, index) in endimion" :key="index">
            {{ item.title }}
      </option
        >
      </datalist>
   
       

      <div v-for="(item, id) in list" :key="id">
        <Card :item="item" />
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Card from "./components/Card.vue";

export default {
  name: "App",

  components: {
    Card,
  },

  data() {
    return {
      endimion: [],
      endimionFive: [],
      input: "",
      list: [],
    };
  },

  created: function() {
    return axios
      .get("https://jsonplaceholder.typicode.com/posts?q=lorem")
      .then((res) => {
        this.endimion = res.data;
      });
  },

  methods: {
    submitTask() {
      if (this.input != "") {
        this.list = [];
        this.endimion.map((person) => {
          if (
            person.title.toLowerCase().includes(this.input) ||
            person.title.toUpperCase().includes(this.input) ||
            person.title.includes(this.input) ||
            person.body.toLowerCase().includes(this.input) ||
            person.body.toUpperCase().includes(this.input) ||
            person.body.includes(this.input)
          ) {
            this.list.push(person);
          }
        });
      }
      this.input = "";
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
