<template>
  <div>
    <b-navbar class="navbar" fixed="top" toggleable="md" type="dark">
      <div class="container">
        <b-navbar-toggle target="nav_collapse" />
      </div>
    </b-navbar>
    <div class="row main">
      <div v-for="item in herois" v-bind:key="item.Id + Math.random()">
        <div class="row card-row">
          <div class="col-3">
            <img v-bind:src="item.img" class="img" />
          </div>

          <div style="text-align: left" class="col-9">
            <p style="font-weight: bold">{{item.name}}</p>
            <p>{{item.description}}</p>
            <p>5 Primeiras histórias: {{item.stories.items[0].name}}, {{item.stories.items[1].name}}, 
              {{item.stories.items[2].name}}, {{item.stories.items[3].name}}, {{item.stories.items[4].name}}</p>
          </div>
        </div>
      </div>
    </div>
    <div class="footer">
      <div class="container">
        <div class="row">
          <a style="color: black" href="http://marvel.com">Data provided by Marvel. © 2018 MARVEL</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script> 

import axios from 'axios'

export default {
  name: 'Home',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      herois: []
    }
  },
  mounted () {
    axios.get(`https://gateway.marvel.com:443/v1/public/characters/1009368?ts=1&apikey=7cf7d13732115f35315922110c51275b&hash=ed1d3d9b32140fba0ef749f90798901f`)
    .then(response => {
      response.data.data.results[0].img = 'https://novomundo.vteximg.com.br/arquivos/ids/904558-1000-1000/SemCaixa.jpg?v=636035926439200000'
      this.herois.push(response.data.data.results[0])
    })
    .catch(e => {
    })
    axios.get(`http://gateway.marvel.com/v1/public/characters/1009268?ts=1&apikey=7cf7d13732115f35315922110c51275b&hash=ed1d3d9b32140fba0ef749f90798901f`)
    .then(response => {
      response.data.data.results[0].img = 'https://m.media-amazon.com/images/S/aplus-media/vc/dbc1c785-96ff-4e48-97bd-9671fb97648e._SL300__.png'
      this.herois.push(response.data.data.results[0])
    })
    .catch(e => {
    })
    axios.get(`https://gateway.marvel.com:443/v1/public/characters/1009610?ts=1&apikey=7cf7d13732115f35315922110c51275b&hash=ed1d3d9b32140fba0ef749f90798901f`)
    .then(response => {
      response.data.data.results[0].img = 'https://img.elo7.com.br/product/original/11FBB76/peso-de-porta-homem-aranha-spider-man-presentes.jpg'
      this.herois.push(response.data.data.results[0])
    })
    .catch(e => {
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.main {
  margin: 80px 50px 80px 50px;
}
.navbar {
  background-image: url(../assets/navbar.jpg);
  background-repeat: repeat-x;
  height: 64px;
  background-position: right top;
}
.card-row {
  border: 2px solid #ddd;
  padding-top: 15px;
  background-color: white;
  padding-bottom: 15px;
  margin-top: 30px;
}
.footer {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  padding: 10px;
  background-color: #ddd;
  z-index: 201;
  border-bottom: 1px solid #ccc;
}
.img {
  height: 200px;
  width: 200px;
}
</style>
