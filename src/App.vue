<template>
  <div id="app">
    <img width="25%" src="./assets/logo.png">
    <HelloWorld msg="Hello Vue in CodeSandbox!"/>

    <div v-for: message="message">{{message.data.time}}</div>
    <p>{{message.data.disclaimer}}</p>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";
import axios from "axios";
export default {
  name: "App",
  components: {
    HelloWorld
  },
  data() {
    return {
      message: []
    };
  },
  mounted() {
    axios
      .get("https://api.coindesk.com/v1/bpi/currentprice.json")
      .then(data => {
        console.log(data);
        return (this.message = data);
      });
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
