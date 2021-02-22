<template>
  <body>
  <div class="sidebar">
    <h3 class="menu">Menu</h3>
    <div class="title">
        <router-link to="/main" class="routerLink">Overall info</router-link>
        <button class="btn" v-on:click="getData()">County</button>
        <button class="btn">Area</button>
        <button class="btn">Projects</button>
        <button class="btn" v-on:click="getData()">Developers</button><br>
    </div>
    <div class="title">
      <router-link to="/main" class="routerLink">Something</router-link>
    </div><br>
    <div class="title">
      <router-link to="/main" class="routerLink">More things</router-link>
    </div>
  </div>

  <div class="body-text">
    <table id="table">
      <tr>
        <th>ID</th>
        <th>Developer name</th>
        <th>Action</th>
      </tr>
      <tr v-for="row in developers">
        <td>{{row.developerId}}</td>
        <td>{{row.developerName}}</td>
        <td>
          <button class="button">Edit</button>
          <button class="button">Delete</button>
        </td>
      </tr>
    </table>
    <br>
    <div class="add">
      <button class="button">Add new county</button>
    </div>
  </div>
  </body>
</template>


<script>
let getData = function () {
  this.$http.get('http://localhost:8080/crawler/alldevelopers')
      .then(response => this.developers = response.data)
}

export default {
  name: 'Main',
  components: {},

  data: function () {
    return {
      developers: []
    }
  },

  methods: {
    getData: getData
  },
}
</script>


<style scoped>
</style>