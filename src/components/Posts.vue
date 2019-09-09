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
          <td>{{ post.title }}</td>
          <td>{{ post.author }}</td>
          <td>{{ post.date }}</td>
          <td>{{ post.body }}</td>
          <td>
              <button>EDIT</button>
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
      posts: Array,
  }
};
</script>

<style scoped>
  button {
    margin: 0.5rem;
  }
</style>