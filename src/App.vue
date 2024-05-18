<template>
  <div id="app" class="app">
    <!-- heading -->
    <header class="app__heading">
      <h1>Books<span>.app</span></h1>
    </header>

    <!-- books list -->
    <books-list
      @remove="removeBook"
      :books="books" />

    <!-- no books message -->
    <!-- <p v-show="!books.length">No books...</p> -->

    <!-- books amount message -->
    <books-length-msg
      :books="books" />

    <!-- add book form -->
    <books-form
      @add="addBook" />

    <!-- books summary -->
    <books-summary
      :books="books" />

  </div>
</template>

<script>
import BooksList from './components/BooksList'
import BooksLengthMsg from './components/BooksLengthMsg'
import BooksForm from './components/BooksForm'
import BooksSummary from './components/BooksSummary'

export default {
  name: 'App',
  data: () => ({
    books: [
      { title: 'The Catcher in the Rye', price: 20 },
      { title: 'Of Mice and Man', price: 18 }
    ]
  }),
  methods: {
    removeBook (index) {
      this.books.splice(index, 1)
    },
    addBook (book) {
      this.books.push({
        ...book
      })
    }
  },
  components: {
    BooksList,
    BooksLengthMsg,
    BooksForm,
    BooksSummary
  }
}
</script>

<style lang="scss" scoped>
.app {
  width: 100%;
  max-width: 1000px;
  padding: 2rem;
  margin: 0 auto;

  &__heading {
    font-size: 3rem;
    text-align: center;
    span {
      color: #5a58da;
    }
  }
}
</style>
