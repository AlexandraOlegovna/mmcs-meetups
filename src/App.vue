<template>
  <div id="app" :class="[!atMain && $root.theme]">

    <header>
      <h1><router-link to="/" :tag="atMain ? 'span' : 'a'" v-text="'mmcs meetups'"/></h1>

      <small class="menu">
        <router-link :to="{ name: 'new' }" v-text="'Организаторам'"/>
        <s href="#">Статистика</s>
        <router-link :to="{ name: 'about' }" v-text="'О сайте'"/>
      </small>
    </header>

    <router-view/>

  </div>
</template>

<script>
  export default {
    name: 'app',
    computed: {
      atMain() { return this.$route.name === 'main' }
    }
  }
</script>

<style scoped>
  h1 {
    font-family: Lora, Roboto, serif;
    padding: 0 0.5em;
    font-size: 2em;
    white-space: nowrap;
    margin-right: 5rem;
    margin-bottom: 0;
    margin-top: 0;
  }

  h1:after {
    content: ' ♥';
    color: #E91E63;
  }

  header {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    align-items: center;
    margin-bottom: 1.34em;
    margin-top: 1.34em;
  }

  @media screen and (max-width: 500px) {
    header { margin-bottom: 0 }
  }

  .menu {
    margin: 0.5rem 1rem;
    color: #444;
  }

  .menu > * {
    color: inherit;
    background-color: #f2f2f2;
    padding: 0.1em 0.3em;
  }

  .menu > *:not(:last-child) {
    margin-right: 0.8em;
  }

  .menu a {
    text-decoration-color: #E91E63;
  }

  .menu > a:hover {
    background-color: #E91E63;
    text-decoration: none;
    color: #fff;
  }
</style>

<style>
  * {
    box-sizing: inherit;
  }

  html, body {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  #app {
    color: #444;
    font-family: 'PT Sans', sans-serif;
    border-top: 6px solid #ade3e6;
    border-top-color: var(--border, #ade3e6);
  }

  @media screen and (min-width: 500px) {
    #app { padding-left: 5% }
  }

  a {
    color: #679e37;
    text-decoration: none;
    cursor: pointer;
  }

  a:hover,a:focus,a:active {
    text-decoration: underline;
  }

  h1 a {
    color: inherit;
  }

  input, textarea, select {
    outline-color: #e91e63;
  }
</style>
