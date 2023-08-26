<template>
  <div class="header   col-sm-12">
    <p id="p" v-show="showUsers"><i class="fa-solid fa-user"></i> USERS</p>
    <p id="p" v-show="showTodos"><i class="fa-solid fa-list"></i> TODOS</p>
    <p id="p" v-show="showAlbum">
      <i class="fa-solid fa-photo-film"></i> ALBUM
    </p>
    <p id="p" v-show="showPhotos"><i class="fa-solid fa-image"></i> PHOTOS</p>
    <p id="p" v-show="showComments">
      <i class="fa-solid fa-comment"></i> COMMENT
    </p>
    <p id="p" v-show="show"><i class="fa-regular fa-address-card"></i> POST</p>
  </div>
</template>

<script>
export default {
  props: [
    "showUsers",
    "showTodos",
    "showAlbum",
    "showPhotos",
    "showComments",
    "show"
  ]
};
</script>

<style scoped>
div {
  height: 80px;
  background-color: #d9d9d9;
}
</style>
