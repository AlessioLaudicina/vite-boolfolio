<template>
     <div class="card my-2" style="width: 18rem;">
              <img class="card-img-top" src="" alt="Card image cap">
                <div class="card-body">
                 <h5 class="card-title">{{ post.title }}</h5>
                 <p class="card-text">{{ truncateText(post.content) }}</p>
                 <a href="#" class="btn btn-primary">Vedi post completo</a>
                </div>
     </div>
</template>


<script>
  import { store } from '../store.js';

export default {
    name: 'ProjectCard',
    props: ['post'],
    data() {
        return {
            contentMaxLength: 200,
            store
        }
    },
    methods: {
        truncateText(text) {
            if (text && text.length > this.contentMaxLength) {
                return text.substr(0, this.contentMaxLength) + '...';
            }
            return text;
        }
    }
};
</script>