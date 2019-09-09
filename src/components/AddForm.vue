<template>
  <div>
    <form @submit.prevent="handleSubmit">
      <label>Title</label>
      <input v-model="post.title" type="text" ref="first" />
      <label>Author</label>
      <input v-model="post.author" type="text" />
      <label>Date</label>
      <input v-model="post.date" type="date" />
      <label>Words ⬇︎</label>
      <input v-model="post.body" type="text" />
      <button>submit</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "add-form",
  data() {
    return {
        post: {
            id: 0,
            title: "",
            author: "",
            date: "",
            body: ""
        },
    }
  },
  methods: {
      handleSubmit() {
          this.$emit('add:post', this.post)
          this.$emit('toggle:form')
          this.$refs.first.focus()
      }
  }
}
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

input {
  max-width: 50vw;
}
</style>