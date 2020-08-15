<template>
  <div class="form__line">
    <h3>{{ title }}</h3>
    <input type="text"
           class="form__input"
           :value="value"
           :name="name"
           autocomplete="off"/>
  </div>
</template>

<script>
export default {
  props: ["title", "value", "name"],
};
</script>

<style scoped>
.form__line {
  width: 100%;
  display: flex;
  justify-content: space-between;
}

.form__input {
  width: 50%;
  height: 40px;
  padding-left: 12px;
  border: 2px solid #c9c9c9;
  border-radius: 5px;
  font-size: 16px;
}
</style>