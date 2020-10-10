<template>
  <div><nuxt-link to="/jokes">Back</nuxt-link>
  <h2>{{joke}}</h2>
  <hr/>
  <small>Joke Id: {{$route.params.id}}</small>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      joke: {},
    };
  },
  async created() {
    const config = {
      headers: {
        Accept: "application/json",
      },
    };
    try {
      const res = await axios.get(`https://icanhazdadjoke.com/j/${this.$route.params.id}`, config);
      this.joke = res.data.joke;
    } catch (err) {
      console.log(err);
    }
  },
};
</script>