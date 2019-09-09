<template>
  <div id="app">
    <Header />
    <img
      id="logo"
      alt="Wheel logo"
      src="./assets/kisspng-mountain-bike-bicycle-wheel-rim-free-bike-che-gulu-pull-material-5a8bd9dd400206.1966990815191147172622.png"
    />
    <HelloWorld msg="A Cycling Blog" />
    <AddForm v-if="show" @add:post="addPost" @toggle:form="toggleForm"/>
    <button v-else @click='toggleForm'>Make a Post</button>
    <Posts :posts="posts" />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import Header from "./components/Header.vue";
import AddForm from "./components/AddForm.vue";
import Posts from "./components/Posts.vue";
export default {
  name: "app",
  components: {
    HelloWorld,
    Header,
    AddForm,
    Posts
  },
  data() {
    return {
      show: false,
      posts: [
      ]
    };
  },
  methods: {
    addPost(post) {
    
      const lastId =
        this.posts.length > 0
          ? this.posts[this.posts.length - 1].id
          : 0;
      const id = lastId + 1;
      const newPost = { ...post, id };
      this.posts = [...this.posts, newPost];
    },
    toggleForm() {
      this.show = !this.show
    }
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
}

#logo {
  max-width: 15vw;
  animation: App-logo-spin infinite 10s linear;
  margin-top: 60px;
}

@keyframes App-logo-spin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

button {
  width: 8rem;
}
</style>
