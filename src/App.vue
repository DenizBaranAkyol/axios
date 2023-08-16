<template>
  <div class="container-fuild" id="app">
    <div class="row">
      <div style="background-color: #DBEADD;" class="col-sm-2">
        <ul class="list-group">
          <li id="element" class="list-group-item " style="height: 80px; border-radius: 10px; background-color: #DBEADD;">
            <i class="fa-solid fa-person-circle-check"></i> APP
          </li>

          <li @click="getPosts" id="element" class=" list-group-item "><i class="fa-regular fa-address-card"></i> posts
          </li>

          <li @click="getComments" id="element" class="list-group-item "><i class="fa-solid fa-comment"></i> comments</li>

          <li @click="getAlbums" id="element" class="list-group-item "><i class="fa-solid fa-photo-film"></i> albums</li>

          <li @click="getPhotos" id="element" class="list-group-item "><i class="fa-solid fa-image"></i> photos</li>

          <li @click="getTodos" id="element" class="list-group-item "><i class="fa-solid fa-list"></i> todos</li>

          <li @click="getUsers" id="element" class="list-group-item "><i class="fa-solid fa-user"></i> users</li>



        </ul>
      </div>
      <div style="margin-left: -15px; background-color: #D9D9D9;" class=" col">
        <div style="height: 80px;  background-color: #D9D9D9;" class="header   col-sm-12">

        

        </div>
        <div style="  background-color: #D9D9D9; " class="header col-sm-12">

          <!-------------------------------------------------------------------------------------------------------------------------->
         
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'app',
    data() {
        return {
            
        };
    },
    methods: {
    
    },
   
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
}

h1,
h2 {
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

#element {
  border-radius: 5px;
  margin: 10px;
  background-color: #C4DCD3;
  font-family: 'Josefin Sans';
  font-size: 22px;
}

#p {
  text-align: center;
  padding-top: 25px;
  font-size: x-large;
}
</style>
