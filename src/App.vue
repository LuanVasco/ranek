<template>
  <div id="app">
    <Header />
    <main id="main">
      <router-view/>
    </main>
    <Footer />
  </div>
</template>

<script>
import Header from "@/components/Header"
import Footer from "@/components/Footer"
export default {
    components: {
      Header,
      Footer
    }
}
</script>

<style>
#app {
  display: flex;
  min-height: 100vh;
  flex-direction: column;
}
#main {
  flex: 1;
}
* {
  box-sizing: border-box;
}
body {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  color: #345;
  background: url('./assets/pattern.svg') repeat top;
}
body, ul, li, h1, h2, p {
  margin: 0;
  padding: 0;
}
ul {
  list-style: none;
}
a {
  color: #345;
  text-decoration: none;
}
img {
  max-width: 100%;
  display: block;
}

.btn {
  display: block;
  padding: 10px 30px;
  background: #87F;
  text-align: center;
  font-size: 1rem;
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  color: #FFF;
  cursor: pointer;
  border-radius: 4px;
  border:none;
  box-shadow:  0 4px 8px rgba(30, 60, 90, 0.2);
  transition: all .3s;
}

.btn:hover {
  background: #65D;
  transform: scale(1.1);
}

input, textarea {
  border-radius: 4px;
  border: 1px solid #fff;
  padding: 15px;
  box-shadow: 0 4px 8px rgba(30, 60, 90, 0.1);
  transition: all .3s;
  font-size: 1rem;
  font-family: "Avenir", Arial, Helvetica, sans-serif;
  margin-bottom: 15px;
}

input:hover, textarea:hover
input:focus, textarea:focus {
  outline: none;
  box-shadow: 0 6px 12px rgba(30, 60, 90, 0.2);
  border-color: #87F;
}
</style>
