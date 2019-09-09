<template>
  <div id="posts">
    <p v-if="posts.length < 1" class="empty-table">No Posts!</p>
    <table v-else>
      <thead>
        <tr>
          <th>Title</th>
          <th>By</th>
          <th>When</th>
          <th>Stuff</th>
          <th>Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="post in posts" :key="post.id">
          <td v-if="editing === post.id" class="title">
            <input type="text" v-model="post.title" />
          </td>
          <td v-else class="title">{{ post.title }}</td>
          <td v-if="editing === post.id" class="author">
            <input type="text" v-model="post.author" />
          </td>
          <td v-else class="author">{{ post.author }}</td>
          <td v-if="editing === post.id" class="date">
            <input type="text" v-model="post.date" />
          </td>
          <td v-else class="date">{{ post.date }}</td>
          <td v-if="editing === post.id" class="body">
            <input type="text" v-model="post.body" />
          </td>
          <td v-else class="body">{{ post.body }}</td>
          <td v-if="editing === post.id" class="btn">
            <button @click="editPost(post)">Save</button>
            <button class="muted-button" @click="editing = null">Cancel</button>
          </td>
          <td v-else class="btn">
            <button @click="editMode(post.id)">EDIT</button>
            <button @click="$emit('delete:post', post.id)">DELETE</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "posts",
  props: {
    posts: Array
  },
  data() {
    return {
      editing: null
    };
  },
  methods: {
    editMode(id) {
      this.editing = id;
    },
    editPost(post) {
      if (
        post.title === "" ||
        post.author === "" ||
        post.date === "" ||
        post.body === ""
      )
        return;
      this.$emit("edit:post", post.id, post);
      this.editing = null;
    }
  }
};
</script>

<style scoped>
button {
  margin: 0.5rem;
}
.btn {
    width: 4vw;
}
.title {
    width: 10vw;
}
.author {
    width: 7vw;
}
.date {
    width: 9vw;
}
.body {
    width: 40vw;
}

</style>