<script>

import axios from 'axios';
import { store } from '../store.js';
import ProjectCard from './ProjectCard.vue';
export default{
    name: "AppMain",
    data() {
        return {
            posts: [],
            contentMaxLength: 200,
            currentPage: 1,
            store
        };
    },
    methods: {
        getPosts(gotoPage) {
            axios.get('${this.store.baseUrl}/api/posts', {
                params: this.currentPage
            })
                .then(response => {
                console.log(response);
                this.posts = response.data.results;
                this.currentPage = response.data.results.currentPage;
            });
        },
        // funzione per troncare il testo delle card
        truncateText(text) {
            if (text && text.length > this.contentMaxLength) {
                return text.substr(0, this.contentMaxLength) + "...";
            }
            return text;
        }
    },
    mounted() {
        this.getPosts(1);
    },
    components: { ProjectCard }
}
</script>

<template>
    <div class="container">
        <div class="row">
            <div class="col-4" v-for="post in posts">
                <ProjectCard :post="post"></ProjectCard>
               

            </div>
        </div>

        <nav aria-label="...">
  <ul class="pagination">
    <li class="page-item disabled">
      <a class="page-link" @click="getPosts(currentPage - 1)" :class="{'disable' : currentPage=1}">Previous</a>
    </li>
    
    <li class="page-item">
      <a class="page-link" @click="getPosts(currentPage + 1)">Next</a>
    </li>
  </ul>
</nav>
    </div>

</template>