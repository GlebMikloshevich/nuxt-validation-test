<template>
  <div>
    <section>
      <h1>auto validation</h1>
      <b-field label="Фамилия*">
        <b-input v-model="lastname"></b-input>
      </b-field>
      <b-field label="Имя*">
        <b-input v-model="name"></b-input>
      </b-field>
      <b-field label="Отчество">
        <b-input v-model="middlename"></b-input>
      </b-field>
      <b-field label="Email*">
        <b-input type="email"></b-input>
      </b-field>
    </section>  </div>
</template>

<script>
export default {
  name: 'auto_validation',
};
</script>

<style scoped>

</style>
