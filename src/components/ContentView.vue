<template>
  <div class="container mt-5">
    <b-card class="mt-2 hasil">
      <!-- <pre class="m-0">{{ results }}</pre> -->
      <h3>{{ results.setup }}</h3>
      <h4>{{ results.punchline }}</h4>
      <b-form @submit.prevent="onSubmit">
        <b-button type="submit" variant="primary">Reload</b-button>
      </b-form>
    </b-card>
  </div>
</template>

<script>
import axios from 'axios'
    export default {
    name: 'ContentView',
    data() {
        return {
            results: '',
        }
    },
    methods: {
        setJokes(data) {
            this.results = data;
        
        },
        onSubmit(event) {
            event.preventDefault()
            axios
                .get('https://official-joke-api.appspot.com/jokes/random')
                .then((response) => this.setJokes(response.data))
                .catch((error) => console.log(error))
        }
    },
    mounted() {
        axios
            .get('https://official-joke-api.appspot.com/jokes/random')
            .then((response) => this.setJokes(response.data))
            .catch((error) => console.log(error))
    }
}
</script>

<style>
.hasil {
  text-align: right;
}
h3 {
  color: #537fe7;
}
h4 {
  color: #3e54ac;
}
</style>