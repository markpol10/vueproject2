<template>
    <div>




            <div v-for="item in list" v-bind:key="item.id" class="container"> 
            <img src="./curiosity.png" class="curiosity">
            <div class="text">
                <p> Name: {{item.name}} </p> 
                <p> Current location: Mars </p>
                 <p> Landing date: {{item.landing_date}} </p>
                 <p> Current status: {{item.status}} </p>
                 <p> Total photos taken: {{item.total_photos}}</p></div>
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
        return{list:undefined}
    },
    mounted() {
        Vue.axios.get('https://api.nasa.gov/mars-photos/api/v1/rovers/curiosity/?api_key=TGMcPguOALpyiCKgjjJ8bUX0rRqChA96JWT4Lwao')
        .then((resp)=>{
            this.list=resp.data;
            console.warn(resp.data)
        })
    }
}
</script>

<style> 


p{
    background: black;
    border: 1px solid red;
    font-size: 12px;
}
.container {
    position: absolute;
    bottom: 100px;
    left: 100px;
    z-index: 2;
    cursor: pointer;
}

.curiosity {
    position: absolute;
    width: 300px;
    z-index: 1;
}

.text {
    opacity: 0;
    font-family: 'helvetica';
    text-align: center;
    width: 250px;
}

.container:hover .text {
    opacity: 1;
    transform: translateY(-150px);
    transition: 1s;
}

</style>