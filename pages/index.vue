<template>
  <div class="container py-5">
    <div class="row justify-content-between">
      <CardItem class="col-md-4" />
      <CardItem class="col-md-4" />
      <CardItem class="col-md-4" />
      <CardItem class="col-md-4" />
      <CardItem class="col-md-4" />
      <CardItem class="col-md-4" />
      <CardItem class="col-md-4" />
      <CardItem class="col-md-4" />
      <CardItem class="col-md-4" />
    </div>
  </div>
</template>

<script>
import CardItem from '~/components/CardItem.vue';

export default {
    name: 'IndexPage',
    components: { CardItem }
}
</script>
