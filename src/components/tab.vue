<template>
  <div :title="title" class="tab">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "tab",
  props:{
    title:{
      type: String,
      default:'',
      required:true
    }
  }
}
</script>

<style scoped>
</style>
