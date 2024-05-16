<template>
  <div id="app">
    <!-- heading -->
    <header>
      <h1>Books<span>.app</span></h1>
    </header>

    <!-- books list -->
    <ul>
      <li
        :key="index"
        v-for="(book, index) in books">
        {{ book.title }}, {{ book.price }}$
        <button @click="removeBook(index)">Remove</button>
      </li>
    </ul>

    <!-- no books message -->
    <p v-show="!books.length">No books...</p>

    <!-- books amount message -->
    <div>
      <p v-if="books.length > 5">There are {{ books.length }} books.</p>
      <p v-else-if="books.length <= 5 && books.length > 1">Not too many of them...</p>
      <p v-else-if="books.length === 1">One single book!</p>
      <p v-else>Go get some books!</p>
    </div>

    <!-- add book form -->
    <form @submit.prevent="addBook">
      <label>
        Title:
        <input v-model="form.title" type="text" name="title">
      </label>
      <label>
        price:
        <input v-model="form.price" type="text" name="price">
      </label>
      <button>Add book</button>
    </form>

  </div>
</template>

<script>
export default {
  name: 'App',
  data: () => ({
    books: [
      { title: 'The Catcher in the Rye', price: 20 },
      { title: 'Of Mice and Man', price: 18 }
    ],
    form: {
      title: '',
      price: 0
    }
  }),
  methods: {
    removeBook (index) {
      this.books.splice(index, 1)
    },
    addBook () {
      this.books.push({
        title: this.form.title,
        price: this.form.price
      })
      this.form.title = ''
      this.form.price = 0
    }
  }
}
</script>
