<template>
  <header>
    <h1>Project Planner</h1>
    <nav class="main-nav">
      <router-link :to="{ name: 'Home' }">Projects</router-link>
      <router-link :to="{ name: 'AddProject' }">Add New Project</router-link>
    </nav>
  </header>
</template>

<script>
export default {};
</script>

<style>
header {
  margin: 20px auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
h1 {
  color: #999;
}
.main-nav {
  text-align: center;
}
.main-nav a {
  display: inline-block;
  text-decoration: none;
  margin: 5px 10px;
  color: #999;
  font-size: 18px;
  font-weight: 700;
}
.main-nav a:hover {
  color: rgba(153, 153, 153, 0.55);
}
a.router-link-active {
  border-bottom: 2px solid #00ce89;
  padding-bottom: 4px;
}
</style>
