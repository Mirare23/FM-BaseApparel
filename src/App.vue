<template>
  <main class="grid h-screen grid-rows-[1fr, 1fr] lg:grid-cols-6">
    <div
      class="fixed self-start w-full px-10 py-10 max-lg:bg-white lg:top-20 lg:px-60 lg:py-0"
    >
      <img
        src="/images/logo.svg"
        height="20"
        width="100"
        class="lg:w-40"
        alt=""
      />
    </div>
    <div
      class="flex flex-col items-start justify-center h-full px-5 max-lg:py-10 lg:col-span-4 lg:py-20 lg:px-60 lg:bg-custom max-lg:order-2"
    >
      <div
        class="flex flex-col justify-center lg:gap-16 max-lg:text-center lg:mt-20"
      >
        <h1
          class="font-light tracking-widest text-8xl max-lg:text-5xl text-Desaturated-Red"
        >
          WE'RE
          <span class="font-normal text-Dark-Grayish-Red">COMING SOON</span>
        </h1>
        <p class="text-sm lg:max-w-lg lg:text-lg text-Desaturated-Red">
          Hello fellow shoppers! We're currently building our new fashion store.
          Add your email below to stay up-to-date with announcements and our
          launch deals.
        </p>
        <div class="relative flex items-center max-lg:mt-10">
          <input
            v-model="email.input"
            type="email"
            placeholder="Email Address"
            class="w-full p-2 px-6 border rounded-full lg:px-6 lg:py-5 focus:outline-none focus:border-red-500"
            required
          />
          <div
            v-if="email.errorMsg"
            class="absolute z-10 flex items-center rounded-full right-40"
          >
            <img src="/images/icon-error.svg" alt="" />
          </div>
          <button
            @click.prevent="checkEmail"
            type="submit"
            class="absolute inset-y-0 flex items-center px-8 rounded-full lg:px-12 bg-gradient-c end-0"
          >
            <img src="/images/icon-arrow.svg" alt="" />
          </button>
          <span
            v-if="email.errorMsg"
            class="absolute inset-0 text-red-500 top-20 start-5"
            >Please provide a valid email</span
          >
        </div>
      </div>
    </div>
    <div class="overflow-hidden lg:col-span-2 max-lg:order-1 max-lg:mt-20">
      <img
        src="/images/hero-desktop.jpg"
        class="object-cover object-left w-full h-full"
        alt=""
      />
    </div>
  </main>
</template>

<script setup lang="ts">
import { ref } from "vue"
const email = ref({
  input: "",
  errorMsg: false,
})

const checkEmail = () => {
  if (email.value.input.indexOf("@") < 0) {
    email.value.errorMsg = true
  }
}
</script>

<style scoped>
.bg-custom {
  background-image: url("/images/bg-pattern-desktop.svg");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
}

.bg-gradient-c {
  background-image: linear-gradient(135deg, hsl(0, 80%, 86%), hsl(0, 74%, 74%));
}
</style>
