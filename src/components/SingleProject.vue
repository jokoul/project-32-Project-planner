<template>
  <!--Conditional styling with binding class-->
  <div class="project" :class="{ complete: project.complete }">
    <div class="actions">
      <h3 @click="showDetails = !showDetails">{{ project.title }}</h3>
      <div class="icons">
        <router-link :to="{ name: 'EditProject', params: { id: project.id } }">
          <button class="crudBtn">
            <span class="material-icons">edit</span>
          </button>
        </router-link>
        <button @click="deleteProject" class="crudBtn">
          <span class="material-icons">delete</span>
        </button>
        <button @click="toggleComplete" class="crudBtn">
          <span class="material-icons tick">done</span>
        </button>
      </div>
    </div>
    <div v-if="showDetails" class="details">
      <p>{{ project.details }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ["project"],
  data() {
    return {
      showDetails: false,
      uri:
        "https://project-planner-json-server.herokuapp.com/projects/" +
        this.project.id, //http://localhost:3000 https://project-planner-json-server.herokuapp.com
    };
  },
  methods: {
    deleteProject() {
      fetch(this.uri, { method: "DELETE" })
        .then(() => this.$emit("delete", this.project.id)) //we create custom event first arg is the name and second the data send along
        .catch((error) => console.log(error.message)); //manage error in case fetch is failed
    },
    toggleComplete() {
      fetch(this.uri, {
        method: "PATCH", //with this method we ca sen only one property to update
        headers: { "Content-Type": "application/json" }, //headers of the request say type of data send is json.
        body: JSON.stringify({ complete: !this.project.complete }), //stringify change the js object data to a json string format before sending
      })
        .then(() => {
          this.$emit("complete", this.project.id);
        })
        .catch((err) => console.log(err.message));
    },
  },
};
</script>

<style>
.project {
  margin: 20px auto;
  background: white;
  padding: 10px 20px;
  border-radius: 4px;
  box-shadow: 1px 2px 3px rgba(0, 0, 0, 0.05);
  border-left: 4px solid #e90074;
}
h3 {
  cursor: pointer;
}
h3:hover {
  color: #999;
}
.actions {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: nowrap;
}
.icons {
  min-width: 40%;
}
.material-icons {
  font-size: 24px;
  margin-left: 10px;
  color: #bbb;
  cursor: pointer;
}
.material-icons:hover {
  color: #777;
}
.project.complete {
  border-left: 4px solid #00ce89;
  transition: all 0.3s ease-in-out;
}
.project.complete .tick {
  color: #00ce89;
  font-weight: 900;
}
.crudBtn {
  background: none;
  border: none;
}
</style>
