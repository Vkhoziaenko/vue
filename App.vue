<template>
  <div id="app">
    <div class="factBox">
      <h1 class="factHeader">Fun Fact</h1>
      <p class="factCategory" v-show="cat">
        Category: {{ cat[0].toUpperCase() + cat.slice(1) }}
      </p>
      <p class="factContent">
        {{ fact }}
      </p>
    </div>
  </div>
</template>

<script>
import Axios from "axios";

export default {
  name: "App",
  data() {
    return {
      fact: "",
      cat: "",
    };
  },
  mounted() {
    Axios.get("https://asli-fun-fact-api.herokuapp.com/").then((res) => {
      this.fact = res.data.data.fact;
      this.cat = res.data.data.cat;
    });
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
html,
body {
  height: 100%;
  margin: 0;
  padding: 0;
}
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100%;
}
.factBox {
  margin: 0 50px;
  border: #f4a460 solid 1px;
  font-size: 30pt;
  text-align: center;
  min-width: 550px;
  background: #ffe4c4;
}
.factHeader {
  background: #f4a460;
}
.factContent {
  padding: 0 5px;
}
</style>
