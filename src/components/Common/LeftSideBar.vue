<template>
  <ul class="list-group">
    <li id="APP" class="list-group-item ">
      <i class="fa-solid fa-person-circle-check"></i> APP
    </li>

    <li @click="getPosts" class=" list-group-item ">
      <i class="fa-regular fa-address-card"></i> Posts
    </li>

    <li @click="getComments" class="list-group-item ">
      <i class="fa-solid fa-comment"></i> Comments
    </li>

    <li @click="getAlbums" class="list-group-item ">
      <i class="fa-solid fa-photo-film"></i> Albums
    </li>

    <li @click="getPhotos" class="list-group-item ">
      <i class="fa-solid fa-image"></i> Photos
    </li>

    <li @click="getTodos" class="list-group-item ">
      <i class="fa-solid fa-list"></i> Todos
    </li>

    <li @click="getUsers" class="list-group-item ">
      <i class="fa-solid fa-user"></i> Users
    </li>
  </ul>
</template>

<script>
export default {
  methods: {
    getPosts() {
      this.$emit("getPosts");
    },
    getComments() {
      this.$emit("getComments");
    },
    getAlbums() {
      this.$emit("getAlbums");
    },
    getPhotos() {
      this.$emit("getPhotos");
    },
    getTodos() {
      this.$emit("getTodos");
    },
    getUsers() {
      this.$emit("getUsers");
    }
  }
};
</script>

<style scoped>
li {
  border-radius: 5px;
  margin: 10px;
  background-color: #c4dcd3;
  font-family: "Josefin Sans";
  font-size: 22px;
}

#APP {
  height: 80px;
  border-radius: 10px;
  background-color: #dbeadd;
}
</style>
