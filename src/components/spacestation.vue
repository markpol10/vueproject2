<template>
 



<div class="isscont">

<h1 style="margin-top: -100px; font-family: 'helvetica'"> Location of ISS </h1> <br> <br> <br>
<img src="./iss.png" class="iss">

    <div class="isstekst" v-for="(value, name) in iss_data" v-bind:key="value">
        <p> {{name}} = {{value}} </p>  
    </div>

    
    
</div>


    
</template>

<script>

import Vue from 'vue';
import axios from 'axios'
import VueAxios from 'vue-axios'

Vue.use(VueAxios,axios)
export default {
    name:"First-component",
    data(){
        return {
            iss_data: {}
        }
    },
    mounted() {
        Vue.axios.get('http://api.open-notify.org/iss-now.json')
        .then((resp)=>{
            this.iss_data=resp.data["iss_position"];
            console.warn(resp.data["iss_position"])
        })

    }
}

</script>

<style> 

.iss {
    height: 170px;
    transform: rotate(-70deg);
}

.isscont {
    position: absolute;
    left: 100px;
    top: 200px;
}

.isscont:hover .isstekst{
    opacity: 1;
    transform: translateY(100px);
    transition: ease 1s;
}

.isscont {
    width: 250px;
    position: absolute;
    top: 200px;
    right: 10vw;
    z-index: 1;
    cursor: pointer;
}

.isstekst {
    opacity: 0;
    width: 250px;
    text-align: center;
}

.isstekst p{
    font-family: 'helvetica';
    margin: 5px;
    border: 1px solid red;
    font-size: 12px;
    background: black;
}

</style>