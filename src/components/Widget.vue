<template>
  <div class="widget">
    <h2>Информация о пользователе</h2>
    <div class="widget__data">
      <p>Фамилия: {{ userData.surname }}</p>
      <p>Имя: {{ userData.name }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ["header", "userData"],
};
</script>

<style>
.widget {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #fff;
  width: 70%;
  border-radius: 10px;
  margin-top: 20px;
  margin-bottom: 20px;
}

.widget__data {
  width: 90%;
  text-align: left;
}
</style>