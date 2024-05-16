<template>
  <div id="app">
    <HeaderComponent/>
    <header id="site-header">
      <nav>
        <router-link to="/">Home</router-link> |
        <router-link to="/books">Books</router-link> |
        <router-link to="/test">Account</router-link>
      </nav>
    </header>
    <router-view/>
    <button v-if="!isTestPage" v-on:click='goToTest'>Test Bitch</button>
    <button v-if="!isHomePage" v-on:click='goToHome'>Home Bitch</button>
    <button v-if="!isBooksPage" v-on:click='goToBooks'>Books Bitch</button>
    <BooksSliderVue/>
  </div>
</template>

<script>
import HeaderComponent from '../src/components/homePageComponents/HeaderComponent.vue';
import BooksSliderVue from './components/booksPageComponents/BooksSlider.vue';


export default {
  components: {
    HeaderComponent,
    BooksSliderVue
  },
  data() {
    return {
      isTestPage: false,
      isHomePage: false,
      isBooksPage: false
    }
  },
  watch: {
    $route() {
      this.isTestPage = this.$route.name === 'test';
      this.isHomePage = this.$route.name === '/';
      this.isAboutPage = this.$route.name === 'books';
    }
  },
  created () {
    this.isTestPage = this.$route.name === 'test';
    this.isBooksPage = this.$route.name === 'books';
    this.isHomePage = this.$route.name === '/';
  },
  methods: {
    goToTest() {
      this.$router.replace({ name: 'test'})
    },
    goToBooks() {
      this.$router.replace({ name: 'books'})
    },
    goToHome() {
      this.$router.replace({ name: '/'})
    }
  }
}

</script>

<style>

@import '../src/assets/globalStyles.css';

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}

#site-header {
  background-color: var(--secondary-colour);
  padding: 10px;
}

nav {
  padding: 10px;
  display: flex;
  flex-direction: row;
  justify-content: center;
  gap: 10px;
}

nav a {
  font-weight: bold;
  color: white;
  text-decoration: none;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
