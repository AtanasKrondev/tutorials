<template>
  <div class="navigation">
    <ul>
      <li v-for="(item, index) in navItems" :key="item.id">
        <a @click="navItemClickHandler(index)">{{item.name}}</a>
      </li>
    </ul>

    <ul>
      <li>
        <a href="#">SUBJECT [+]</a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    navItems: {
      type: Array,
      required: true
    }
  },
  methods: {
    navItemClickHandler(index) {
      this.$emit("navigate", index);
    }
  }
};
</script>

<style scoped>
main div.navigation {
  background: #44a9f8;
  font-size: 20px;
  text-align: left;
  display: flex;
}

main div.navigation ul {
  display: inline-block;
  text-align: left;
}

main div.navigation ul:nth-child(1) {
  width: 75%;
}

main div.navigation ul:nth-child(2) {
  width: 20%;
  text-align: right;
}

main div.navigation li {
  list-style: none;
  display: inline-block;
  margin-right: 3%;
}

main div.navigation ul:nth-child(2) li {
  width: 100%;
}

main div.navigation li a {
  padding: 1%;
  color: white;
  text-decoration: none;
  font-weight: bold;
}

main div.navigation li a:hover {
  text-decoration: underline;
}
</style>