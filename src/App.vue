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
import axios from 'axios'

export default {
  name: 'App',
  data: () => ({
    books: []
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
  },
  created () {
    const corsAnywhereUrl = 'https://cors-anywhere.herokuapp.com/'
    const apiUrl = 'https://api.itbook.store/1.0/search/javascript'

    axios.get(corsAnywhereUrl + apiUrl)
      .then(response => {
        this.books = response.data.books.slice(0, 3).map(book => ({
          title: book.title,
          price: book.price.replace('$', '')
        }))
      })
      .catch(error => {
        this.error = 'Failed to load books. Please try again later.'
        console.error(error)
      })
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
