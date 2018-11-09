<template>
  <div class="container">
    <h1>Tasks page</h1>
    <div class="section">
      <ul>
        <li>{{ person.name }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  asyncData(context) {
    return axios.get('https://swapi.co/api/people/1/')
    .then(res => {
      console.log('response data: ', res.data)
      return {
        person: {... res.data}
      }
    })
  }
}
</script>
