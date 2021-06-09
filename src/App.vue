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
</style>
