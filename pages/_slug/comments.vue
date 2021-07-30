<template>
  <div>
    <h1>Comments Page with this slug parameterś</h1>
    <p>{{ $route.params.slug }}</p>
  </div>
</template>

<script>
export default {
  validate({ params }) {
    // Must be Number
    
    return /^\d+$/.test(params.slug)
  },
}
</script>
