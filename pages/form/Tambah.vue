<template>
  <div class="container">
    <form id="tambah-artikel" @submit.prevent="onFormSubmit">
      <div class="form-group">
        <label for="title">Judul Artikel</label>
        <input id="title" type="text" class="form-control" name="title">
      </div>
      <div class="form-group">
        <label for="content">Example textarea</label>
        <textarea id="content" class="form-control" name="content" rows="3"></textarea>
      </div>

      <button class="btn btn-primary" type="submit">Tambah Artikel</button>
    </form>
  </div>
</template>

<script>
import httpClient from "~/utils/httpClient"

export default {
  data() {
    return {}
  },
  methods: {
    async onFormSubmit() {
      const dataForm = {
        title: document.getElementById("title").value,
        content: document.getElementById("content").value,
      }
      const response = await httpClient("/rest/v1/articles", "POST", JSON.stringify(dataForm))
      
      const data =  await response?.json()
      this.$router.push(`/detail/${data[0]?.id}`)
    }
  }
}
</script>
