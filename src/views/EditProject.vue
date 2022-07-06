<template>
  <div>
    <form @submit.prevent="editProject">
      <label>Title</label>
      <input v-model="title" type="text" required />
      <label>Details</label>
      <textarea v-model="details" required></textarea>
      <button>Update Project</button>
    </form>
  </div>
</template>

<script>
export default {
  props: ["id"],
  data() {
    return {
      // id: this.$route.params.id,
      title: "",
      details: "",
      complete: false,
      uri: "https://project-planner-joan.herokuapp.com/projects/" + this.id, //proxy : http://localhost:3000.
    };
  },
  mounted() {
    fetch(this.uri)
      .then((res) => res.json())
      .then((data) => {
        // console.log(data);
        (this.title = data.title),
          (this.details = data.details),
          (this.complete = data.complete);
      })
      .catch((err) => console.log(err.message));
  },
  methods: {
    editProject() {
      fetch(this.uri, {
        method: "PATCH",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({
          title: this.title,
          details: this.details,
          // complete: this.complete,
        }),
      })
        .then(() => this.$router.push({ name: "Home" }))
        .catch((err) => console.log(err.message));
    },
  },
};
</script>

<style></style>
