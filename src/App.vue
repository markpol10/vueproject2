
<template>

<div class="page-container">

  <div> 
  <peoplespace />
  <firstcomponent />
  <spacestation />
  </div>

<div class="mars"></div>

  <img src="./components/world.png" class="world"> 


</div>

</template>

<script>

import firstcomponent from './components/FirstComponent'
import peoplespace from './components/peoplespace'
import spacestation from './components/spacestation'
export default {
  name: "App",
  components: {
    peoplespace,
    firstcomponent,
    spacestation
  }
};



</script>

<style>



body {
  margin: 0;
  padding: 0;
  color: white;

}

.page-container {
  width: 100vw;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  background: radial-gradient(circle, rgba(63,94,251,1) 0%, rgba(43,57,129,1) 19%, rgba(27,27,27,1) 64%);
}

.world {
  position: absolute;
  height: 400px;
  z-index: 0;
}

.world:hover {
  transform: rotate(20deg);
  transition: 0.5s;
}

.mars {
  position: absolute;
  bottom: 0;
  height: 50px;
  width: 100vw;
  background: rgba(161, 110, 74, 1);
  z-index: 0;
}



</style>
