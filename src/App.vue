<template>
  <div class="container-fuild" id="app">
    <div class="row">
      <div id="leftSideBar" class="col-sm-2">
        <!-- LEFT SİDE BAR -->
        <appLeftSideBar @getPosts="getPosts" @getComments="getComments" @getAlbums="getAlbums" @getPhotos="getPhotos"
          @getTodos="getTodos" @getUsers="getUsers">
        </appLeftSideBar>
      </div>
      <div id="header" class=" col">
        <!-- HEADER -->
        <appHeader :showUsers="showUsers" :show="showPost" :showComments="showComment" :showAlbum="showAlbum"
          :showPhotos="showPhotos" :showTodos="showTodos"></appHeader>
        <div id="tables" class="header col-sm-12">
        </div>
        <!-- TABLE -->

        <appTableComponent :todosData="Todos.data" :usersData="Users.data" :photosData="Photos.data"
          :albumsData="Albums.data" :gelenData="gelenData" :commentsData="Comments.data" :show="showPost"
          :postData="Posts.data">
        </appTableComponent>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import TableComponent from "./components/Tables/TableComponent.vue";
import LeftSideBar from "./components/Common/LeftSideBar.vue";
import Header from "./components/Common/Header.vue";
export default {
  name: "app",
  data() {
    return {
      showUsers: false,
      showTodos: false,
      showAlbum: false,
      showPhotos: false,
      showComment: false,
      showPost: false,
      gelenData: null,
      Posts: {
        data: null,
      },
      Comments: {
        data: null
      },
      Albums: {
        data: null
      },
      Photos: {
        data: null
      },
      Todos: {
        data: null
      },
      Users: {
        data: null
      }
    };
  },

  methods: {
    getPosts: function () {
      axios.get(`https://jsonplaceholder.typicode.com/posts`).then(response => {
        this.Posts.data = response.data;
        console.log(Object.keys(this.Posts.data[0])[0]);
        this.showPost = true;
        (this.showComment = false), (this.showAlbum = false);
        this.showPhotos = false;
        this.showTodos = false;
        this.showUsers = false;
        this.showComment = false;
        this.showAlbum = false;
        this.gelenData = false
        this.gelenData = "post"
      }
      );


    },
    getComments: function () {
      axios
        .get(`https://jsonplaceholder.typicode.com/comments`)
        .then(response => {
          this.Comments.data = response.data;
          this.showPost = false;
          this.showComment = true;
          this.showAlbum = false;
          this.showPhotos = false;
          this.showTodos = false;
          this.showUsers = false;
          this.gelenData = "comments"
        });
    },
    getAlbums: function () {
      axios
        .get(`https://jsonplaceholder.typicode.com/albums`)
        .then(response => {
          this.Albums.data = response.data;
          this.showPost = false;
          this.showComment = false;
          this.showAlbum = true;
          this.showPhotos = false;
          this.showTodos = false;
          this.showUsers = false;
          this.gelenData = "albums"
        });
    },
    getPhotos: function () {
      axios
        .get(`https://jsonplaceholder.typicode.com/photos`)
        .then(response => {
          this.Photos.data = response.data;
          this.showPost = false;
          this.showComment = false;
          this.showAlbum = false;
          this.showPhotos = true;
          this.showTodos = false;
          this.showUsers = false;
          this.gelenData = "photos"
        });
    },
    getTodos: function () {
      axios.get(`https://jsonplaceholder.typicode.com/todos`).then(response => {
        this.Todos.data = response.data;
        this.showPost = false;
        this.showComment = false;
        this.showAlbum = false;
        this.showPhotos = false;
        this.showTodos = true;
        this.showUsers = false;
        this.gelenData = "todos"
      });
    },
    getUsers: function () {
      axios.get(`https://jsonplaceholder.typicode.com/users`).then(response => {
        this.Users.data = response.data;
        this.showPost = false;
        this.showComment = false;
        this.showAlbum = false;
        this.showPhotos = false;
        this.showTodos = false;
        this.showUsers = true;
        this.gelenData = "users"
      });
    }
  },
  components: {
    appTableComponent: TableComponent,
    appLeftSideBar: LeftSideBar,
    appHeader: Header,
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
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

#p {
  text-align: center;
  padding-top: 25px;
  font-size: x-large;
}

#leftSideBar {
  background-color: #dbeadd;
}

#header {
  margin-left: -15px;
  background-color: #d9d9d9;
}

#tables {
  background-color: #d9d9d9;
}
</style>
