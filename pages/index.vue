<template>
<section class="container">
  <div>
    <logo />
    <h1 class="title">
      nuxt-todoist
    </h1>
    <h2 class="subtitle">
      Providing alternate views and sorting for TODOist tasks
    </h2>
    <div class="links">
      <a
          href="https://tasks/"
          target="_blank"
          class="button--green">TODOist tasks</a>
      <a
          :href="
          this.authURL +
          '?client_id=' +
          this.clientID +
          '&scope=data:read' +
          '&state=' +
          this.state"
          target="_blank"
          class="button--grey">TODOist auth</a>
    </div>
  </div>
</section>
</template>

<script>
import Logo from '~/components/Logo.vue'
import axios from 'axios'

export default {
  components: {
    Logo
  },
  created: function () {
    console.log('test created hook')
    axios.get('https://swapi.co/api/people/1/')
      .then(res => {
        console.log(res.data)
      })

  },
  methods: {
    runAuth() {
      console.log('runAuth running')
      axios.get(
          this.authURL +
          '?client_id=' +
          this.clientID +
          '&scope=data:read' +
          '&state=' +
          this.state
        )
        .then(res => {
          console.log(res.data)
        })
    }
  },
  data() {
    return {
      clientID: 'ea192b83308a4580b068497defed4b60',
      clientSecret: 'c9bb957808464542b70b67e11fa056e8',
      authURL: 'https://todoist.com/oauth/authorize',
      state: 'mikessecret'
    }
  }
}
</script>

<style>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
