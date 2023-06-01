
<script>
import { store } from '../store.js';
import axios from 'axios';

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
        // funzione per troncare il testo delle card
        truncateText(text) {
            if (text && text.length > this.contentMaxLength) {
                return text.substr(0, this.contentMaxLength) + '...';
            }
            return text;
        }
    }
};
</script>

<template>
    <div class="card my-2" style="width: 18rem;">

        <img v-if="post.cover_image" :src="`${this.store.baseUrl}/storage/${post.cover_image}`" class="card-img-top">
        <img v-else src="data:image/png;base64,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" class="card-img-top"/>
               <div class="card-body">
                <h5 class="card-title">{{post.title}}</h5>
                <h5>{{post.category?.name}}</h5>
                <p class="card-text">{{ truncateText(post.content) }}</p>
                <router-link :to="{name: 'SingleProject', params: {slug: post.slug}}" class="btn btn-primary">Vedi progetto</router-link>
               </div>
    </div>
</template>