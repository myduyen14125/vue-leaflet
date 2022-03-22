<template>
  <div class="card brew-list">
    <ul class="list-group list-group-flush">
      <li v-for="brew in brews" class="list-group-item" :key="brew.id">
        {{ brew.name }}, {{ brew.state }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "List",
  props: {
    brews: Array,
  }
  
};
</script>
<style lang="scss" scoped>
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
  transition: 0.3s;
  &:hover {
    background: rgb(170, 170, 170);
  }
}
.brew-list {
  overflow-x: hidden;
  height: 90vh;
}
</style>