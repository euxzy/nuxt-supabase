<template>
  <div class="p-3">
    <div class="card">
      <img src="https" class="card-img-top" alt="...">
      <div class="card-body">
        <h5 class="card-title">{{ title }}</h5>
        <p class="card-text text-truncate">{{ description }}</p>
        <nuxt-link :to="`/detail/${articleId}`" class="btn btn-primary">Go somewhere</nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      default: ""
    },
    description: {
      type: String,
      default: ""
    },
    articleId: {
      type: String,
      default: ""
    },
  }
}
</script>
