<template>
  <header>
    <h1>{{newTitle}}</h1>
  </header>
</template>

<script>
export default {
  name: "header2",
  props: {
    title: String
  },
  data() {
    return {
      name: "Beatrix"
    };
  },
  computed: {
    newTitle: function() {
      console.log(this);

      return this.name + " Ducz";
    }
  }
};
</script>

<style scoped>
header {
  background-color: #111;
  padding: 20px;
  color: #fff;
}
h1 {
  margin: 0;
}
</style>