<template>
  <Products :products="this.category.products" :error="error" />
</template>

<script>
import Products from "~/components/Products.vue"

export default {
  data() {
    return {
      category: {},
      error: null
    }
  },
  async mounted() {
    try {
       const res = await fetch(`http://localhost:1337/categories/${this.$route.params.id}`)
      this.category = await res.json()
    } catch (error) {
      console.log(error)
      console.log(typeof(error))
      // this.error = error
    }
  },
  components: {
    Products
  }
}
</script>
