<template>
    <div class="container">
        <v-card
            v-for="article of articles"
            :key="article.id"
            class="mx-auto"
            max-width="344">
            <a :href="article.url" target="_blank">
                <v-img :src="article.cover_image">
                </v-img>
            </a>
            <v-card-text>
                <v-card-title>
                    {{article.title}}
                </v-card-title>
            </v-card-text>
            <v-card-actions class="pt-0">
                <v-btn
                    text
                    color="teal accent-4"
                    target="_blank"
                    :href="article.url">
                    Read <v-icon>external-link</v-icon>
                </v-btn>
            </v-card-actions>
        </v-card>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    props: {
        userName: {
            type: String,
            default: 'venatus'
        }
    },
    data() {
        return {
            articles: []
        }
    },

    methods: {
        async getArticles() {
            return axios.get(`https://dev.to/api/articles?username=${this.userName}`);
        },
    },

    async created() {
        this.articles = (await this.getArticles())
            .data
            .filter(article => article.type_of ==='article');
    }
}
</script>

<style lang="scss" scoped>
    .container {
        display: flex;
        flex-direction: column;
        gap: 20px;
    }
</style>