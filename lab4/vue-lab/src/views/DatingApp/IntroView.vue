<script setup lang="ts">
import { ref } from 'vue';
import { useRouter } from 'vue-router';
import MeetNewPeople from '@/views/DatingApp/MeetNewPeople.vue';
import ChatWIithEase from '@/views/DatingApp/ChatWIithEase.vue'
import FatedLoginRegister from '@/views/DatingApp/FatedLoginRegister.vue'

const router = useRouter();
const currentStep = ref(1);

const nextStep = () => {
  if (currentStep.value < 3) {
    currentStep.value++;
  }
};

const prevStep = () => {
  if (currentStep.value > 1) {
    currentStep.value--;
  }
};

const skipOnboarding = () => {
  currentStep.value = 3;
};
</script>

<template>
  <div class="w-full h-[calc(100vh-80px)] flex flex-col items-center relative overflow-hidden no-scroll">

    <div
      v-if="currentStep === 3"
      class="fixed inset-0 bg-[#FF5F5F] z-0"
    ></div>

    <div class="relative z-10 w-full h-full flex justify-center">

      <MeetNewPeople
        v-if="currentStep === 1"
        @next="nextStep"
        @skip="skipOnboarding"
      />

      <ChatWIithEase
        v-if="currentStep === 2"
        @next="nextStep"
        @prev="prevStep"
        @skip="skipOnboarding"
      />

      <FatedLoginRegister
        v-if="currentStep === 3"
        class="h-full"
      />
    </div>

  </div>
</template>

<style scoped></style>
