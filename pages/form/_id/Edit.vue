<template>
  <div class="container">
    <form id="tambah-artikel" @submit.prevent="onFormSubmit">
      <input id="id" v-model="articleId" type="hidden" class="form-control" name="id">
      <div class="form-group">
        <label for="title">Judul Artikel</label>
        <input id="title" v-model="title" type="text" class="form-control" name="title">
      </div>
      <div class="form-group">
        <label for="content">Example textarea</label>
        <textarea id="content" v-model="content" class="form-control" name="content" rows="3"></textarea>
      </div>

      <button class="btn btn-primary" type="submit">Tambah Artikel</button>
    </form>
  </div>
</template>

<script>
import httpClient from "~/utils/httpClient"

export default {
  data() {
    return {
      title: "",
      content: "",
      articleId: "",
    }
  },
  mounted() {
    const params = this.$route.params
    this.getDetailData(params?.id)
  },
  methods: {
    async getDetailData(articleId) {
      const response = await httpClient("/rest/v1/articles?id=eq." + articleId, "GET")

      const data = await response.json()

      this.title = data[0]?.title
      this.content = data[0]?.content
      this.articleId = data[0]?.id
    },
    async onFormSubmit() {
      const dataForm = {
        title: document.getElementById("title").value,
        content: document.getElementById("content").value,
      }
      const response = await httpClient("/rest/v1/articles?id=eq." + this.articleId, "PATCH", JSON.stringify(dataForm))
      
      const data =  await response?.json()
      this.$router.push(`/detail/${data[0]?.id}`)
    }
  }
}
</script>
