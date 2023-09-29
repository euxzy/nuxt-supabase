<template>
  <div class="container py-5">
    <div class="row justify-content-between">
      <CardItem
        v-for="(item, idx) of articles"
        :key="idx"
        :title="item?.title"
        :description=item?.content
        :article-id="item?.id"
        class="col-md-4"
      />
    </div>
  </div>
</template>

<script>
// import httpClient from "~/utils/httpClient"
import CardItem from '~/components/CardItem.vue'

export default {
    name: 'IndexPage',
    components: { CardItem },
    
    data() {
      return {
        articles: [],
      }
    },
    mounted() {
      this.getArticles();
    },
    methods: {
      async getArticles() {
        const response = await this.$axios.get("/rest/v1/articles", {
          headers: {
            apikey: process.env.supabaseKey
          }
        })

        this.articles = response?.data
      },
    }
}
</script>
