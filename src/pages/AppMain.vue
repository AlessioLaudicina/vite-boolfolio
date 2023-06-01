<script>

import axios from 'axios';
import { store } from '../store.js';
import ProjectCard from '../components/ProjectCard.vue';
export default{
    name: "AppMain",
    data() {
        return {
            posts: [],
            currentPage: 1,
            lastPage: null,
            store
        };
    },
    methods: {
        getPosts(gotoPage) {
            axios.get(`${this.store.baseUrl}/api/posts`, {
                params: {
                    page: gotoPage
                }
            })
                .then(response => {
                console.log(response);
                this.posts = response.data.results.data;
                this.currentPage = response.data.results.currentPage;
                this.lastPage = response.data.results.last_page;
            });
        },
    },
    mounted() {
        this.getPosts(1);
    },
    components: { ProjectCard },
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
    <li class="page-item">
      <button class="page-link" @click="getPosts(currentPage - 1)" :class="{'disable' : currentPage=1}">Previous</button>
    </li>
    
    <li class="page-item">
      <button class="page-link" @click="getPosts(currentPage + 1)" :class="{'disabled' : currentPage == lastPage}">Next</button>
    </li>
  </ul>
</nav>
    </div>

</template>