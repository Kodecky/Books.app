<template>
  <div>
      <p v-if="books.length > 5">There are {{ books.length }} books.</p>
      <p v-else-if="books.length <= 5 && books.length > 1">Not too many of them...</p>
      <p v-else-if="books.length === 1">One single book!</p>
      <p v-else>Go get some books!</p>
    </div>
</template>

<script>
export default {
  name: 'BooksLengthMsg',
  props: {
    books: {
      type: Array,
      required: true
    }
  }
}
</script>
