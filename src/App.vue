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

          <p id="p" v-show="showUsers"> <i class="fa-solid fa-user"></i> USERS</p>
          <p id="p" v-show="showTodos"> <i class="fa-solid fa-list"></i> TODOS</p>
          <p id="p" v-show="showAlbum"> <i class="fa-solid fa-photo-film"></i> ALBUM</p>
          <p id="p" v-show="showPhotos"> <i class="fa-solid fa-image"></i> PHOTOS</p>
          <p id="p" v-show="showComment"> <i class="fa-solid fa-comment"></i> COMMENT</p>
          <p id="p" v-show="showPost"> <i class="fa-regular fa-address-card"></i> POST</p>

        </div>
        <div style="  background-color: #D9D9D9; " class="header col-sm-12">

          <!-------------------------------------------------------------------------------------------------------------------------->
          <table v-show="showUsers" class="table table-hover table-success table-striped">
            <thead>
              <tr>
                <th scope="col">ID</th>
                <th scope="col">Name</th>
                <th scope="col">User Name</th>
                <th scope="col">Email</th>
                <th scope="col">Adress</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="user in Users.data">
                <th scope="row">{{ user.id }}</th>
                <td>{{ user.name }}</td>
                <td>{{ user.username }}</td>
                <td>@{{ user.email }}</td>
                <td>@{{ user.address.street + " " + user.address.suite + " " + user.address.city + " " +
                  user.address.zipcode }}</td>
              </tr>
            </tbody>
          </table>

          <!---------------------------------------------------------------------------------------------------------------------------->

          <table v-show="showPost" class="table table-hover table-success table-striped">
            <thead>
              <tr>
                <th scope="col">ID</th>
                <th scope="col">TİTLE</th>
                <th scope="col">BODY</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="user in Posts.data">
                <th scope="row">{{ user.id }}</th>
                <td>{{ user.title }}</td>
                <td>{{ user.body }}</td>
              </tr>
            </tbody>
          </table>

          <!---------------------------------------------------------------------------------------------------------------------------->

          <table v-show="showComment" class="table table-hover table-success table-striped">
            <thead>
              <tr>
                <th scope="col">ID</th>
                <th scope="col">NAME</th>
                <th scope="col">EMAİL</th>
                <th scope="col">BODY</th>
                <th scope="col">POST ID</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="user in Comments.data">
                <th scope="row">{{ user.id }}</th>
                <td>{{ user.name }}</td>
                <td>{{ user.email }}</td>
                <td>{{ user.body }}</td>
                <td>{{ user.postId }}</td>
              </tr>
            </tbody>
          </table>

          <!---------------------------------------------------------------------------------------------------------------------------->

          <table v-show="showAlbum" class="table table-hover table-success table-striped">
            <thead>
              <tr>
                <th scope="col">ıD</th>
                <th scope="col">TİTLE</th>
                <th scope="col">USER ID</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="user in Albums.data">
                <th scope="row">{{ user.id }}</th>
                <td>{{ user.title }}</td>
                <td>{{ user.userId }}</td>
              </tr>
            </tbody>
          </table>

          <!---------------------------------------------------------------------------------------------------------------------------->

          <table v-show="showPhotos" class="table table-hover table-success table-striped">
            <thead>
              <tr>
                <th scope="col">ID</th>
                <th scope="col">ALBUM ID</th>
                <th scope="col">TİTLE</th>
                <th scope="col">PHOTOS</th>
                <th scope="col">THUMBNAİL URL</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="user in Photos.data">
                <th scope="row">{{ user.id }}</th>
                <td>{{ user.albumId }}</td>
                <td>{{ user.title }}</td>
                <td> <img v-bind:src="user.url" width="50px" height="50px" alt=""></td>
                <td>{{ user.thumbnailUrl }}</td>
              </tr>
            </tbody>
          </table>

          <!---------------------------------------------------------------------------------------------------------------------------->

          <table v-show="showTodos" class="table table-hover table-success table-striped">
            <thead>
              <tr>
                <th scope="col">ID</th>
                <th scope="col">USER ID</th>
                <th scope="col">TİTLE</th>
                <th scope="col">COMPLETED</th>

              </tr>
            </thead>
            <tbody>
              <tr v-for="user in Todos.data">
                <th scope="row">{{ user.id }}</th>
                <td>{{ user.userId }}</td>
                <td>{{ user.title }}</td>
                <td> <input v-if="user.completed" type="checkbox" name="" id="" checked>
                  <input v-else type="checkbox" name="" id="">
                </td>
              </tr>
            </tbody>
          </table>
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
            postData: {
                id: null,
                title: null,
                body: null,
            },
            showUsers: false,
            showTodos: false,
            showAlbum: false,
            showPhotos: false,
            showComment: false,
            showPost: false,
            Posts: {
                data: null,
            },
            Comments: {
                data: null,
            },
            Albums: {
                data: null
            },
            Photos: {
                data: null,
            },
            Todos: {
                data: null,
            },
            Users: {
                data: null,
            }
        };
    },
    methods: {
        getPosts: function () {
            axios.get(`https://jsonplaceholder.typicode.com/posts`)
                .then(response => {
                this.Posts.data = response.data;
                this.showPost = true;
                this.showComment = false,
                    this.showAlbum = false;
                this.showPhotos = false;
                this.showTodos = false;
                this.showUsers = false;
            });
        },
        getComments: function () {
            axios.get(`https://jsonplaceholder.typicode.com/comments`)
                .then(response => {
                this.Comments.data = response.data;
                this.showPost = false;
                this.showComment = true,
                    this.showAlbum = false;
                this.showPhotos = false;
                this.showTodos = false;
                this.showUsers = false;
            });
        },
        getAlbums: function () {
            axios.get(`https://jsonplaceholder.typicode.com/albums`)
                .then(response => {
                this.Albums.data = response.data;
                this.showPost = false;
                this.showComment = false;
                this.showAlbum = true;
                this.showPhotos = false;
                this.showTodos = false;
                this.showUsers = false;
            });
        },
        getPhotos: function () {
            axios.get(`https://jsonplaceholder.typicode.com/photos`)
                .then(response => {
                this.Photos.data = response.data;
                this.showPost = false;
                this.showComment = false,
                    this.showAlbum = false;
                this.showPhotos = true;
                this.showTodos = false;
                this.showUsers = false;
            });
        },
        getTodos: function () {
            axios.get(`https://jsonplaceholder.typicode.com/todos`)
                .then(response => {
                this.Todos.data = response.data;
                this.showPost = false;
                this.showComment = false;
                this.showAlbum = false;
                this.showPhotos = false;
                this.showTodos = true;
                this.showUsers = false;
            });
        },
        getUsers: function () {
            axios.get(`https://jsonplaceholder.typicode.com/users`)
                .then(response => {
                this.Users.data = response.data;
                this.showPost = false;
                this.showComment = false;
                this.showAlbum = false;
                this.showPhotos = false;
                this.showTodos = false;
                this.showUsers = true;
            });
        },
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
