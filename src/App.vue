<template>
  <div id="app">
    <Widget v-bind:userData="userData" />
    <Form v-bind:userData="userData" />
  </div>
</template>

<script>
import Widget from "./components/Widget";
import Form from "./components/Form";

export default {
  name: "App",
  data() {
    return {
      headers: ["Информация о пользователе", "Редактирование"],
      userData: [],
    };
  },
  mounted() {
    fetch("https://jsonplaceholder.typicode.com/users/1")
      .then((res) => res.json())
      .then((res) => {
        const arr = res.name.split(" ");
        this.userData = { name: arr[0], surname: arr[1] };
      })
      .catch((err) => console.log(err));
  },
  components: {
    Widget,
    Form,
  },
};
</script>

<style>
#app {
  box-sizing: border-box;
  width: 70%;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  background-color: #e9e9e9;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 30px 30px 90px 30px;
}
body {
  margin: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
