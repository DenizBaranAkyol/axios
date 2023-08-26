<template>
  <div>
    <table class="table table-hover table-success table-striped">
      <!-- console.log(Object.keys(this.Posts.data[0])[0]); -->
      <thead>
        <tr>
          <th v-for="keys in  Object.keys(this.gelenData[0])" scope="col">{{ keys }}</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in gelenData">
          <th v-if="user.userId != null" scope="row">{{ user.userId }}</th>
          <td v-if="user.postId != null">{{ user.postId }}</td>
          <td v-if="user.id != null">{{ user.id }}</td>
          <td v-if="user.title != null">{{ user.title }}</td>
          <td v-if="user.name != null">{{ user.name }}</td>
          <td v-if="user.username != null">{{ user.username }}</td>
          <td v-if="user.email != null">{{ user.email }}</td>
          <td v-if="user.body != null">{{ user.body }}</td>
          <td v-if="user.address != null">{{ user.address }}</td>
          <td v-if="user.phone != null">{{ user.phone }}</td>
          <td v-if="user.website != null">{{ user.website }}</td>
          <td v-if="user.company != null">{{ user.company }}</td>
          <td v-if="user.thumbnailUrl != null">{{ user.thumbnailUrl }}</td>
          <td v-if="user.albumId != null">{{ user.albumId }}</td>
          <td v-if="user.url != null">
            <img v-bind:src="user.url" width="50px" height="50px" alt="" />
          </td>
          <td v-if="user.completed != null">
            <input v-if="user.completed" type="checkbox" name="" id="" checked />
            <input v-else type="checkbox" name="" id="" />
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
<script>
export default {

  updated() {
    if (this.gelenData == "post") {
      this.gelenData = this.postData
    }
    else if (this.gelenData == "comments") {
      this.gelenData = this.commentsData
    }
    else if (this.gelenData == "albums") {
      this.gelenData = this.albumsData
    }
    else if (this.gelenData == "photos") {
      this.gelenData = this.photosData
    }
    else if (this.gelenData == "users") {
      this.gelenData = this.usersData
    }
    else if (this.gelenData == "todos") {
      this.gelenData = this.todosData
    }
  },

  props: ["postData", "gelenData", "commentsData", "albumsData", "photosData", "usersData", "todosData"],

};
</script>
