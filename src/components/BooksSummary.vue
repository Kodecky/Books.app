<template>
  <div>
    <p>Books amount: {{ books ? books.length : 0 }}</p>
    <p>Books price: {{ books ?  summaryPrice : 0 }}</p>
  </div>
</template>

<script>
export default {
  name: 'BooksSummary',
  props: {
    books: {
      type: Array,
      required: true
    }
  },
  computed: {
    summaryPrice () {
      return this.books.reduce((acc, book) => acc + parseFloat(book.price), 0)
    }
  }
}
</script>
