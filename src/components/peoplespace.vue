<template>
 



<div class="cont">

<h1 style="margin-top: -100px; font-family: 'helvetica'"> People in space </h1> <br> <br> <br>
<img src="./astro.png" class="astro">
    <div class="tekst" v-for="item in list" v-bind:key="item.id">
        <p>{{item.name}}   --  {{item.craft}}</p>
    </div>
    
</div>


    
</template>

<script>
import Vue from 'vue';
import axios from 'axios'
import VueAxios from 'vue-axios'

Vue.use(VueAxios,axios)
export default {
    name: "First-component",
    data(){
        return {
            list: undefined
        }
    },
    mounted() {
        Vue.axios.get('http://api.open-notify.org/astros.json')
        .then((resp)=>{
            this.list=resp.data.people;
            console.warn(resp.data.people)
        })
    }
}
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

.astro {
    height: 205px;
    position: absolute;
    transform: rotate(15deg);
    text-align: center;
    margin-top: -40px
}

.tekst {
    opacity: 0;
    width: 250px;
    text-align: center;
}

.tekst p{
    font-family: 'helvetica';
    margin: 5px;
    border: 1px solid red;
    font-size: 12px;
    background: black;
}

.cont:hover .tekst{
    opacity: 1;
    transform: translateY(125px);
    transition: ease 1s;
}


</style>