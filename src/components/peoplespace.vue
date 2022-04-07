<template>
  <div class="cont">
    <h1 style="margin-top: -100px; font-family: 'helvetica'">
      People in space
    </h1>

    <img src="./astro.png" class="astronautImage" />
    <div class="peopleText" v-for="item in list" v-bind:key="item.id">
      <p>{{ item.name }} -- {{ item.craft }}</p>
    </div>
  </div>
</template>

<script>
import Vue from "vue";
import axios from "axios";
import VueAxios from "vue-axios";

Vue.use(VueAxios, axios);
export default {
  name: "First-component",
  data() {
    return {
      list: undefined,
    };
  },
  mounted() {
    Vue.axios.get("http://api.open-notify.org/astros.json").then((resp) => {
      this.list = resp.data.people;
    });
  },
};
</script>

<style>
.cont {
  width: 250px;
  position: absolute;
  top: 200px;
  right: 10vw;
  z-index: 1;
  cursor: pointer;
}

.astronautImage {
  height: 250px;
  position: absolute;
  transform: rotate(15deg);
  text-align: center;
}

.peopleText {
  opacity: 0;
  width: 250px;
  text-align: center;
}

.peopleText p {
  font-family: "helvetica";
  margin: 5px;
  border: 1px solid red;
  font-size: 12px;
  background: black;
}

.cont:hover .peopleText {
  opacity: 1;
  transform: translateY(125px);
  transition: ease 1s;
}
</style>
