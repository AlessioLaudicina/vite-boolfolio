<script>

import axios from 'axios';
export default{
    name: 'AppMain',
    data(){
        return {
            posts:[]

        }
    },
    methods: {
        getPosts(){
            console.log('Forza inter')
            axios.get('http://localhost:8000/api/posts')
            .then(response => {
                console.log(response);
                this.posts = response.data.results;
            })

        }

    },
    mounted(){
        this.getPosts();
    }
}
</script>

<template>
    <div class="container">
        <div class="row">
            <div class="col-4" v-for="post in posts">
                <div class="card" style="width: 18rem;">
              <img class="card-img-top" src="" alt="Card image cap">
               <div class="card-body">
                 <h5 class="card-title">{{ post.title }}</h5>
                 <p class="card-text">{{ post.content }}</p>
                 <a href="#" class="btn btn-primary">Vedi post completo</a>
                </div>
             </div>

            </div>
        </div>
    </div>

</template>