<template>
<div class="container">
<h1 class="title">Albums de la pagina</h1>
<div class="columns is-multiline">
<AlbumCard :album="album" v-for="album in albums" :key="album.id"/>
</div>
</div>
</template>

<script>

import axios from 'axios';
import env from '../config/env';
import AlbumCard from '../components/AlbumCard';
export default {
    name: 'indexPage',
    components:{
        AlbumCard
    },
    data(){
    return{
        albums: []
        }
    },
    created: async function (){
      let response = await axios.get(`${env.endpoint}/albums`)
      this.albums = response.data;
    }
}
</script>


<style scoped>
.title{
    text-align: center;
}
</style>