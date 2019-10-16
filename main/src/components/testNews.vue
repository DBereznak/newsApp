<template>
  <div>
    <h1>test</h1>
    <ul>
        <li v-for="article in newsData">
            <img :src="article.urlToImage" width="500px" height="auto" />
            <h4>{{article.title}}</h4>
            <a :href="article.url">Click to full article</a>
            <p>{{article.content}}</p>
        </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";
import config from "../config/config";

export default {
  name: "testNews",
  data() {
    return {
      newsData: [],
      API_KEY: config.NEWS_API_KEY
    };
  },
  methods: {
    getNews() {
      axios
        .get(
          `https://newsapi.org/v2/top-headlines?country=us&apiKey=${this.API_KEY}`
        )
        .then(response => {
          this.newsData = response.data.articles;
          console.log(this.newsData);
        })
        .catch(error => {
          console.error(error);
        });
    }
  },
  created() {
    this.getNews();
  }
};
</script>

<style scoped></style>
