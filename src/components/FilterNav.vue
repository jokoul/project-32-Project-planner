<template>
  <nav class="filter-nav">
    <button @click="updateFilter('all')" :class="{ active: current === 'all' }">
      View All
    </button>
    <button
      @click="updateFilter('completed')"
      :class="{ active: current === 'completed' }"
    >
      Completed
    </button>
    <button
      @click="updateFilter('ongoing')"
      :class="{ active: current === 'ongoing' }"
    >
      Ongoing
    </button>
  </nav>
</template>

<script>
export default {
  props: ["current"],
  methods: {
    updateFilter(by) {
      this.$emit("filterChange", by);
    },
  },
};
</script>

<style>
.filter-nav button {
  background: none;
  border: none;
  color: #999;
  font-weight: 600;
  outline: none;
  font-size: 14px;
  text-transform: uppercase;
  margin-right: 10px;
  letter-spacing: 1px;
  cursor: pointer;
}
.filter-nav button:hover {
  color: rgba(153, 153, 153, 0.55);
}
/**you can not apply the class only but add before button or .filter-nav button */
button.active {
  color: #555;
  font-weight: 800;
}
</style>
