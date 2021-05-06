<template>
  <div>
    <section>
      <form @submit.prevent="onSubmit()" class="mt-6" method="post">
        <h1 class="mb-1 is-size-3">Auto validation</h1>
        <b-field label="Фамилия*"
                 :type = "data.lastname.type"
                 :message="data.lastname.message"
        >
          <b-input v-model="lastname"
                   @input="check_lastname()"
          ></b-input>
        </b-field>
        <b-field label="Имя*"
                 :type = "data.firstname.type"
                 :message="data.firstname.message"
        >
          <b-input v-model="firstname"
                   @input="check_firstname()"
          ></b-input>
        </b-field>
        <b-field label="Отчество"
                 :type = "data.patronymic.type"
                 :message="data.patronymic.message"
        >
          <b-input v-model="patronymic"
                   @input="check_patronymic()"></b-input>
        </b-field>
        <b-field label="Email*"
                 :type = "data.email.type"
                 :message="data.email.message"
        >
          <b-input type="email" v-model="email"
                   @input="check_email()"></b-input>
        </b-field>

        <b-field label="Password*"
                 :type = "data.password.type"
                 :message="data.password.message"
        >
          <b-input type="password" v-model="password"
                   @input="check_password()"></b-input>
        </b-field>

        <b-button @click="submit">Register</b-button>
      </form>
    </section>
  </div>
</template>

<script>
// eslint-disable-next-line import/no-extraneous-dependencies,no-unused-vars
import { ToastProgrammatic as Toast } from 'buefy';

export default {
  name: 'auto_validation',
  data() {
    return {
      data: {
        errors: false,
        firstname: {
          type: '', message: '', is_error: false, value: '',
        },
        lastname: {
          type: '', message: '', is_error: false, value: '',
        },
        patronymic: {
          type: '', message: '', is_error: false, value: '',
        },
        email: {
          type: '', message: '', is_error: false, value: '',
        },
        password: {
          type: '', message: '', is_error: false, value: '',
        },
      },
    };
  },
  methods: {
    check_lastname() {
      if (!this.lastname || this.lastname.length < 2 || !/^[a-zA-Zа-яА-ЯёЁ'][a-zA-Z-а-яА-ЯёЁ' ]+[a-zA-Zа-яА-ЯёЁ']?$/.test(this.lastname.trim())) {
        this.data.lastname.is_error = true;
        this.data.lastname.type = 'is-danger';
        this.data.lastname.message = 'Поле введено неверно';
        this.data.errors = true;
      } else {
        this.data.lastname.is_error = false;
        this.data.lastname.type = '';
        this.data.lastname.message = '';
        this.data.lastname.value = this.lastname.trim();
      }
    },
    check_firstname() {
      if (!this.firstname || this.firstname.length < 2 || !/^[a-zA-Zа-яА-ЯёЁ'][a-zA-Z-а-яА-ЯёЁ' ]+[a-zA-Zа-яА-ЯёЁ']?$/.test(this.firstname.trim())) {
        this.data.firstname.is_error = true;
        this.data.firstname.type = 'is-danger';
        this.data.firstname.message = 'Поле введено неверно';
        this.data.errors = true;
      } else {
        this.data.firstname.is_error = false;
        this.data.firstname.type = '';
        this.data.firstname.message = '';
        this.data.firstname.value = this.firstname.trim();
      }
    },
    check_patronymic() {
      if (this.patronymic && (this.patronymic.length < 2 || !/^[a-zA-Zа-яА-ЯёЁ'][a-zA-Z-а-яА-ЯёЁ' ]+[a-zA-Zа-яА-ЯёЁ']?$/.test(this.patronymic.trim()))) {
        this.data.patronymic.is_error = true;
        this.data.patronymic.type = 'is-danger';
        this.data.patronymic.message = 'Поле введено неверно';
        this.data.errors = true;
      } else {
        this.data.patronymic.is_error = false;
        this.data.patronymic.type = '';
        this.data.patronymic.message = '';
        this.data.patronymic.value = this.patronymic ? this.patronymic.trim() : '';
      }
    },
    check_email() {
      if (!this.email || this.email.length < 6 || !/^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}?$/.test(this.email.trim())) {
        this.data.email.is_error = true;
        this.data.email.type = 'is-danger';
        this.data.email.message = 'Поле введено неверно';
        this.data.errors = true;
      } else {
        this.data.email.is_error = false;
        this.data.email.type = '';
        this.data.email.message = '';
        this.data.email.value = this.email.trim();
      }
    },
    check_password() {
      if (!this.password || this.password.length < 8) {
        this.data.password.is_error = true;
        this.data.password.type = 'is-danger';
        this.data.password.message = 'Поле введено неверно';
        this.data.errors = true;
      } else {
        this.data.password.is_error = false;
        this.data.password.type = '';
        this.data.password.message = '';
        this.data.password.value = this.password.trim();
      }
    },
    submit() {
      this.data.errors = false;
      this.check_lastname();
      this.check_firstname();
      this.check_patronymic();
      this.check_email();
      this.check_password();
      if (this.data.errors) {
        Toast.open('check errors');
      } else {
        Toast.open('success');
      }
    },
  },
};
</script>

<style scoped>

</style>
