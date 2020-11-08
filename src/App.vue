<template>
  <div class="container mt-4">
    <div class="row">
    <div class="col-sm-4 mx-auto">
    <form @submit.prevent="registerUser" novalidate>
      
      <div v-show="step === 1" class="step">
  <div class="form-group">
    <label for="name">Ваше имя</label>
    <input v-model="formReg.name" type="text" class="form-control" id="name" placeholder="Имя">
  </div>

  <div class="form-group">
    <label for="surname">Ваша фамилия</label>
    <input v-model="formReg.surname" type="text" class="form-control" id="surname" placeholder="Фамилия">
  </div>

    <div class="form-group">
    <label for="email">Почта</label>
    <input v-model="formReg.email" type="text" class="form-control" id="email" placeholder="Почта">
  </div>

  <button @click="nextStep" type="button" class="btn btn-warning">Следующий шаг</button>
      </div>

      <transition name="slide-fade">
  <div v-show="step === 2" class="step">
  <div class="form-group">
    <label for="password">Пароль</label>
    <input v-model="formReg.password" type="password" class="form-control" id="password">
  </div>

  <div class="form-group">
    <label for="passwordConfirm">Подверждение пароля</label>
    <input v-model="formReg.passwordConfirm" type="password" class="form-control" id="passwordConfirm">
  </div>

  <button @click="backStep" type="button" class="btn btn-dark mr-2">Назад</button>
  <button @click="nextStep" type="button" class="btn btn-warning">Следующий шаг</button>
      </div>
      </transition>

 <transition name="slide-fade">
         <div v-show="step === 3" class="step">
  <div class="form-group">
    <label for="country">Страна</label>
    <input v-model="formReg.country" type="text" class="form-control" id="country">
  </div>

  <div class="form-group">
    <label for="city">Город</label>
    <input v-model="formReg.city" type="text" class="form-control" id="city">
  </div>

  <button @click="backStep" type="button" class="btn btn-dark mr-2">Назад</button>
  <button type="submit" class="btn btn-warning">Зарегистрироваться</button>
      </div>
 </transition>
</form>
    </div>
  </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      step: 1,
      formReg: {
        name: '',
        surname: '',
        email: '',
        password: '',
        passwordConfirm: '',
        country: '',
        city: ''
      }
    }
  },
  methods: {
    nextStep() {
      if (this.step <3) {
        this.step++
      }
    },
    backStep() {
      if (this.step > 1) {
        this.step--
      }
    },
    registerUser() {
      console.log('Регистрация прошла успешно!')
      console.log(this.formReg.name)
      console.log(this.formReg.surname)
      console.log(this.formReg.email)
      console.log(this.formReg.password)
      console.log(this.formReg.passwordConfirm)
      console.log(this.formReg.country)
      console.log(this.formReg.city)
    }
  }
}
</script>

<style>
.slide-fade-enter-active {
  transition: all 0.3s ease;
}

.slide-fade-enter {
  transform: translateX(10px);
  opacity: 0;
}
</style>
