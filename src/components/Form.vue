<template>
  <div class="widget">
    <h2>Редактирование</h2>
    <form id="form">
      <FormLine title="Фамилия" v-bind:value="userData.surname" />
      <FormLine title="Имя" v-bind:value="userData.name" />
      <div class="form__buttons">
        <button class="form__button form__button_save">Сохранить</button>
        <button type="reset" class="form__button form__button_reset">Отменить</button>
      </div>
    </form>
  </div>
</template>

<script>
import FormLine from "./FormLine";

export default {
  props: ["userData"],
  components: {
    FormLine,
  },
};
</script>

<style scoped>
#form {
  width: 90%;
}

.form__buttons {
    position: relative;
    top: 70px;
    left: -6%;
}

.form__button {
    width: 120px;
    height: 50px;
    margin-right: 18px;
    border-radius: 5px;
    cursor: pointer;
}

.form__button_reset {
    background-color: #fff;
    border: 2px solid #c9c9c9;
}

.form__button_save {
    background-color: #d11e1e;
    color: #fff;
    border: 0;
}
</style>