<template>
  <div id="app">
    <h1>IMKB Ortalama Hesaplama VueJS</h1>
    <CalculatorForm />
    <AppFooter />
  </div>
</template>

<script>
import CalculatorForm from "@/components/CalculatorForm";
import Footer from "@/components/Footer";
export default {
  name: "App",
  components: {
    CalculatorForm,
    AppFooter: Footer,
  },
};
</script>

<style lang="scss">
* {
  outline: none !important;
}
:root {
  --primary: #41b883;
}
body {
  height: 100vh;
  overflow: hidden;
  margin: 0;
  display: flex;
  align-items: stretch;
  justify-content: center;
  flex-direction: column;
}
#app {
  height: 100vh;
  display: flex;
  align-items: stretch;
  justify-content: center;
  flex-direction: column;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding-top: 30px;
  background: var(--primary);
  img {
    width: 150px;
    margin: 30px;
  }
}
</style>
