<template>
  <div class="issContent">
    <h1 style="margin-top: -100px; font-family: 'helvetica'">
      Location of ISS
    </h1>

    <img src="./iss.png" class="iss" />

    <div class="issText" v-for="(value, name) in iss_data" v-bind:key="value">
      <p>{{ name }} = {{ value }}</p>
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
      iss_data: {},
    };
  },
  mounted() {
    Vue.axios.get("http://api.open-notify.org/iss-now.json").then((resp) => {
      this.iss_data = resp.data["iss_position"];
    });
  },
};
</script>

<style>
.iss {
  height: 170px;
  transform: rotate(-70deg);
  margin-top: 60px
}

.issContent {
  position: absolute;
  left: 100px;
  top: 200px;
}

.issContent:hover .issText {
  opacity: 1;
  transform: translateY(100px);
  transition: ease 1s;
}

.issContent {
  width: 250px;
  position: absolute;
  top: 200px;
  right: 10vw;
  z-index: 1;
  cursor: pointer;
}

.issText {
  opacity: 0;
  width: 250px;
  text-align: center;
}

.issText p {
  font-family: "helvetica";
  margin: 5px;
  border: 1px solid red;
  font-size: 12px;
  background: black;
}
</style>
