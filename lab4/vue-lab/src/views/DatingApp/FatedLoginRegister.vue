<script setup lang="ts">
import { ref, reactive } from 'vue';

const isRegister = ref(true);

const form = reactive({
  username: '',
  password: '',
  email: ''
});

const errors = reactive({
  username: '',
  password: '',
  email: ''
});

const clearError = (field: 'username' | 'password' | 'email') => {
  errors[field] = '';
};

const toggleMode = () => {
  isRegister.value = !isRegister.value;
  form.username = '';
  form.password = '';
  form.email = '';
  errors.username = '';
  errors.password = '';
  errors.email = '';
};

const handleSubmit = () => {
  errors.username = '';
  errors.password = '';
  errors.email = '';

  let isValid = true;

  if (!form.username.trim()) {
    errors.username = "Введіть ім'я!";
    isValid = false;
  }

  if (!form.password) {
    errors.password = "Введіть пароль!";
    isValid = false;
  } else if (form.password.length < 4) {
    errors.password = "Мінімум 4 символи!";
    isValid = false;
  }

  if (isRegister.value) {
    if (!form.email) {
      errors.email = "Введіть email!";
      isValid = false;
    } else if (!form.email.includes('@')) {
      errors.email = "Некоректний email (треба @)";
      isValid = false;
    }
  }

  if (!isValid) {
    console.warn('Validation Failed:', errors);
    return;
  }

  console.group('%c  Form Submitted!', 'color: green; font-weight: bold; font-size: 14px;');
  console.log('Mode:', isRegister.value ? 'Registration' : 'Login');
  console.log('Data:', JSON.parse(JSON.stringify(form))); // Чистий об'єкт даних
  console.groupEnd();

  alert(`Дані успішно відправлені в консоль!\nUser: ${form.username}`);
};
</script>

<template>
  <div class="w-full max-w-[414px] mx-auto flex flex-col items-center justify-evenly py-4 relative h-full">

    <div class="flex flex-col items-center">
      <img src="/images/heart_for_screen.png" alt="Logo" class="w-[110px] object-contain mb-2" />
      <h1 class="font-['Cherry_Bomb_One'] text-[45px] text-white tracking-wide leading-none">
        FATED
      </h1>
    </div>

    <div class="w-[90%] max-w-[330px] flex justify-between">
      <button
        @click="toggleMode"
        :class="isRegister
          ? 'bg-white text-[#FF5F5F] hover:shadow-[0_0_15px_rgba(255,255,255,0.6)]'
          : 'bg-[#FF7A7A] text-white hover:bg-[#ff8585]'"
        class="w-[48%] h-[45px] rounded-[10px] font-extrabold text-[15px] shadow-sm transition-all duration-300"
      >
        REGISTER
      </button>

      <button
        @click="toggleMode"
        :class="!isRegister
          ? 'bg-white text-[#FF5F5F] hover:shadow-[0_0_15px_rgba(255,255,255,0.6)]'
          : 'bg-[#FF7A7A] text-white hover:bg-[#ff8585]'"
        class="w-[48%] h-[45px] rounded-[10px] font-extrabold text-[15px] shadow-sm transition-all duration-300"
      >
        LOGIN
      </button>
    </div>

    <div class="w-[90%] max-w-[330px] flex flex-col gap-2">

      <div class="w-full">
        <input
          v-model="form.username"
          @input="clearError('username')"
          type="text"
          placeholder="user name"
          :class="errors.username ? '!border-red-800 border-2' : ''"
          class="w-full h-[50px] rounded-[10px] px-4 border-2 border-transparent outline-none
                 text-center text-[16px] text-[#32323C] placeholder-gray-400 font-sans shadow-sm bg-white"
        />
        <p v-if="errors.username" class="text-white text-[11px] font-bold text-center mt-1 bg-red-800/20 rounded">
          {{ errors.username }}
        </p>
      </div>

      <div class="w-full">
        <input
          v-model="form.password"
          @input="clearError('password')"
          type="password"
          placeholder="password"
          :class="errors.password ? '!border-red-800 border-2' : ''"
          class="w-full h-[50px] rounded-[10px] px-4 border-2 border-transparent outline-none
                 text-center text-[16px] text-[#32323C] placeholder-gray-400 font-sans shadow-sm bg-white"
        />
        <p v-if="errors.password" class="text-white text-[11px] font-bold text-center mt-1 bg-red-800/20 rounded">
          {{ errors.password }}
        </p>
      </div>

      <div v-if="isRegister" class="w-full">
        <input
          v-model="form.email"
          @input="clearError('email')"
          type="email"
          placeholder="email"
          :class="errors.email ? '!border-red-800 border-2' : ''"
          class="w-full h-[50px] rounded-[10px] px-4 border-2 border-transparent outline-none
                 text-center text-[16px] text-[#32323C] placeholder-gray-400 font-sans shadow-sm bg-white"
        />
        <p v-if="errors.email" class="text-white text-[11px] font-bold text-center mt-1 bg-red-800/20 rounded">
          {{ errors.email }}
        </p>
      </div>

      <a href="#" class="text-right text-[11px] !text-white font-bold hover:underline tracking-wide mt-1">
        FORGOT PASSWORD?
      </a>

      <button
        @click="handleSubmit"
        class="w-full h-[55px] bg-white text-[#FF5F5F] rounded-[10px]
               font-extrabold text-[18px] mt-2 shadow-md transition-all duration-300
               hover:bg-gray-50 hover:shadow-[0_0_20px_rgba(255,255,255,0.5)]"
      >
        {{ isRegister ? 'REGISTER' : 'LOGIN' }}
      </button>
    </div>

    <p class="text-[12px] text-white font-medium tracking-wide">
      {{ isRegister ? 'ALREADY HAVE AN ACCOUNT?' : "DON'T HAVE AN ACCOUNT?" }}
      <a href="#" @click.prevent="toggleMode" class="font-extrabold underline ml-1 cursor-pointer !text-white hover:text-gray-100">
        {{ isRegister ? 'LOGIN' : 'REGISTER' }}
      </a>
    </p>

  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Cherry+Bomb+One&family=Lato:wght@400;800&display=swap');
</style>
