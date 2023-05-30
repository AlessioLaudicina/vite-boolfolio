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

        </div>
    </div>

</template>