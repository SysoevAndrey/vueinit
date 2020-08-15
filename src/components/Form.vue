<template>
  <div class="widget">
    <h2>Редактирование</h2>
    <form id="form" @submit.prevent="onSubmit">
      <FormLine title="Фамилия"
                v-bind:value="userData.surname"
                v-bind:name="names[0]" />
      <FormLine title="Имя"
                v-bind:value="userData.name"
                v-bind:name="names[1]" />
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
  data() {
    return {
      newUserData: { name: this.userData.name, surname: this.userData.surname },
      names: ['surname', 'name'],
      newName: '',
      newSurname: ''
    };
  },
  components: {
    FormLine,
  },
  methods: {
    onSubmit(submitEvent) {
      this.newName = submitEvent.target.elements.name.value;
      this.newSurname = submitEvent.target.elements.surname.value;
      const result = this.newName + " " + this.newSurname;

      fetch("https://jsonplaceholder.typicode.com/users/1", {
        method: "PUT",
        body: JSON.stringify({
          name: `${result}`,
        }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
        },
      })
        .then((res) => res.json())
        .then(() => {
          this.$emit('update-data', this.newName, this.newSurname);
        })
        .catch((err) => console.log(err));
    },

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