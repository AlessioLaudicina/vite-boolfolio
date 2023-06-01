<script>

import axios from 'axios';
import { store } from '../store.js';
   export default{
    name: 'SingleProject',
    data(){
        return {
            posts: [],
            store

        }
    },
    mounted(){
        const slug = this.$route.params.slug
        axios.get(`${this.store.baseUrl}/api/posts/${slug}`, {
               
            })
                .then(response => {
                console.log(response);
                this.posts = response.data.post;
            });
    }
   }
</script>


<template>
     <div class="container">
      <h1>Single Project</h1>


    </div>
    
</template>