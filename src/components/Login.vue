<template>
  <div>
    <div
      @click="closeModal"
      class="fixed bg-black/60 top-0 left-0 w-full h-screen z-10"
    ></div>
    <div
      class="fixed bg-white top-1/2 left-1/2 rounded -translate-x-1/2 -translate-y-1/2 w-[500px] p-5 z-20"
    >
      <div class="flex justify-end">
        <button @click="closeModal">X</button>
      </div>
      <div class="flex justify-center divide-x-2 divide-green-600">
        <button
          @click="content = 'login'"
          class="py-1 px-5"
          :class="{ 'text-green-600': content === 'login' }"
        >
          Login
        </button>
        <button
          @click="content = 'register'"
          class="py-1 px-5"
          :class="{ 'text-green-600': content === 'register' }"
        >
          Register
        </button>
      </div>
      <div v-if="content === 'login'">
        <div class="p-6">
          <h2 class="text-center text-2xl font-bold mb-4">Login</h2>
          <form @submit.prevent="login">
            <div class="mb-4">
              <input
                type="email"
                id="email"
                v-model="email"
                placeholder="Email"
                class="px-2 mt-1 block w-full rounded-md shadow-sm h-[40px] outline-none border focus:border-green-600"
                required
              />
            </div>
            <div class="mb-4">
              <input
                type="password"
                id="password"
                v-model="password"
                placeholder="Password"
                class="px-2 mt-1 block w-full rounded-md shadow-sm h-[40px] outline-none border focus:border-green-600"
                required
              />
            </div>
            <div class="mb-4 text-right">
              <a href="#" class="text-sm text-green-600 hover:underline"
                >Forgot Password?</a
              >
            </div>
            <div class="flex justify-center">
              <button
                type="submit"
                class="bg-green-600 text-white py-2 px-4 rounded-md w-[500px] h-[40px]"
              >
                Login
              </button>
            </div>
          </form>
          <div class="mt-4 text-center">
            <p>Or login with</p>
            <div class="flex flex-col items-center gap-4 mt-2">
              <button
                class="flex items-center justify-center gap-2 py-2 px-4 rounded-md w-[300px] h-[40px] border border-gray-300"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="20"
                  height="20"
                  viewBox="0 0 256 262"
                >
                  <path
                    fill="#4285f4"
                    d="M255.878 133.451c0-10.734-.871-18.567-2.756-26.69H130.55v48.448h71.947c-1.45 12.04-9.283 30.172-26.69 42.356l-.244 1.622l38.755 30.023l2.685.268c24.659-22.774 38.875-56.282 38.875-96.027"
                  />
                  <path
                    fill="#34a853"
                    d="M130.55 261.1c35.248 0 64.839-11.605 86.453-31.622l-41.196-31.913c-11.024 7.688-25.82 13.055-45.257 13.055c-34.523 0-63.824-22.773-74.269-54.25l-1.531.13l-40.298 31.187l-.527 1.465C35.393 231.798 79.49 261.1 130.55 261.1"
                  />
                  <path
                    fill="#fbbc05"
                    d="M56.281 156.37c-2.756-8.123-4.351-16.827-4.351-25.82c0-8.994 1.595-17.697 4.206-25.82l-.073-1.73L15.26 71.312l-1.335.635C5.077 89.644 0 109.517 0 130.55s5.077 40.905 13.925 58.602z"
                  />
                  <path
                    fill="#eb4335"
                    d="M130.55 50.479c24.514 0 41.05 10.589 50.479 19.438l36.844-35.974C195.245 12.91 165.798 0 130.55 0C79.49 0 35.393 29.301 13.925 71.947l42.211 32.783c10.59-31.477 39.891-54.251 74.414-54.251"
                  />
                </svg>
                Login with Google
              </button>
              <button
                class="py-2 px-4 rounded-md w-[300px] h-[40px] border border-gray-300 flex items-center justify-center gap-2"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="20"
                  height="20"
                  viewBox="0 0 256 256"
                >
                  <path
                    fill="#1877f2"
                    d="M256 128C256 57.308 198.692 0 128 0C57.308 0 0 57.308 0 128c0 63.888 46.808 116.843 108 126.445V165H75.5v-37H108V99.8c0-32.08 19.11-49.8 48.348-49.8C170.352 50 185 52.5 185 52.5V84h-16.14C152.959 84 148 93.867 148 103.99V128h35.5l-5.675 37H148v89.445c61.192-9.602 108-62.556 108-126.445"
                  />
                  <path
                    fill="#fff"
                    d="m177.825 165l5.675-37H148v-24.01C148 93.866 152.959 84 168.86 84H185V52.5S170.352 50 156.347 50C127.11 50 108 67.72 108 99.8V128H75.5v37H108v89.445A128.959 128.959 0 0 0 128 256a128.9 128.9 0 0 0 20-1.555V165z"
                  />
                </svg>
                Login with Facebook
              </button>
            </div>
          </div>
        </div>
      </div>
      <div v-if="content === 'register'">
        <div class="p-6">
          <h2 class="text-center text-2xl font-bold mb-4">Register</h2>
          <form @submit.prevent="register">
            <div class="mb-4">
              <label
                for="username"
                class="block text-sm font-medium text-gray-700"
              ></label>
              <input
                type="text"
                id="username"
                v-model="username"
                placeholder="Username"
                class="px-2 mt-1 block w-full rounded-md shadow-sm h-[40px] outline-none border focus:border-green-600"
                required
              />
            </div>
            <div class="mb-4">
              <label
                for="reg-email"
                class="block text-sm font-medium text-gray-700"
              ></label>
              <input
                type="email"
                id="reg-email"
                placeholder="Email"
                v-model="regEmail"
                class="px-2 mt-1 block w-full rounded-md shadow-sm h-[40px] outline-none border focus:border-green-600"
                required
              />
            </div>
            <div class="mb-4">
              <input
                type="password"
                id="reg-password"
                v-model="regPassword"
                placeholder="Password"
                class="px-2 mt-1 block w-full rounded-md shadow-sm h-[40px] outline-none border focus:border-green-600"
                required
              />
            </div>
            <div class="mb-4">
              <input
                type="password"
                id="confirm-password"
                v-model="confirmPassword"
                placeholder="Confirm you Password"
                class="px-2 mt-1 block w-full rounded-md shadow-sm h-[40px] outline-none border focus:border-green-600"
                required
              />
            </div>
            <div class="flex justify-center">
              <button
                type="submit"
                class="bg-green-600 text-white py-2 px-4 rounded-md w-[500px] h-[40px]"
              >
                Register
              </button>
            </div>
          </form>
          <div class="mt-4 text-center">
            <p>Or register with</p>
            <div class="flex flex-col items-center gap-4 mt-2">
              <button
                class="flex items-center justify-center gap-2 py-2 px-4 rounded-md w-[300px] h-[40px] border border-gray-300"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="20"
                  height="20"
                  viewBox="0 0 256 262"
                >
                  <path
                    fill="#4285f4"
                    d="M255.878 133.451c0-10.734-.871-18.567-2.756-26.69H130.55v48.448h71.947c-1.45 12.04-9.283 30.172-26.69 42.356l-.244 1.622l38.755 30.023l2.685.268c24.659-22.774 38.875-56.282 38.875-96.027"
                  />
                  <path
                    fill="#34a853"
                    d="M130.55 261.1c35.248 0 64.839-11.605 86.453-31.622l-41.196-31.913c-11.024 7.688-25.82 13.055-45.257 13.055c-34.523 0-63.824-22.773-74.269-54.25l-1.531.13l-40.298 31.187l-.527 1.465C35.393 231.798 79.49 261.1 130.55 261.1"
                  />
                  <path
                    fill="#fbbc05"
                    d="M56.281 156.37c-2.756-8.123-4.351-16.827-4.351-25.82c0-8.994 1.595-17.697 4.206-25.82l-.073-1.73L15.26 71.312l-1.335.635C5.077 89.644 0 109.517 0 130.55s5.077 40.905 13.925 58.602z"
                  />
                  <path
                    fill="#eb4335"
                    d="M130.55 50.479c24.514 0 41.05 10.589 50.479 19.438l36.844-35.974C195.245 12.91 165.798 0 130.55 0C79.49 0 35.393 29.301 13.925 71.947l42.211 32.783c10.59-31.477 39.891-54.251 74.414-54.251"
                  />
                </svg>
                Login with Google
              </button>
              <button
                class="py-2 px-4 rounded-md w-[300px] h-[40px] border border-gray-300 flex items-center justify-center gap-2"
              >
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  width="20"
                  height="20"
                  viewBox="0 0 256 256"
                >
                  <path
                    fill="#1877f2"
                    d="M256 128C256 57.308 198.692 0 128 0C57.308 0 0 57.308 0 128c0 63.888 46.808 116.843 108 126.445V165H75.5v-37H108V99.8c0-32.08 19.11-49.8 48.348-49.8C170.352 50 185 52.5 185 52.5V84h-16.14C152.959 84 148 93.867 148 103.99V128h35.5l-5.675 37H148v89.445c61.192-9.602 108-62.556 108-126.445"
                  />
                  <path
                    fill="#fff"
                    d="m177.825 165l5.675-37H148v-24.01C148 93.866 152.959 84 168.86 84H185V52.5S170.352 50 156.347 50C127.11 50 108 67.72 108 99.8V128H75.5v37H108v89.445A128.959 128.959 0 0 0 128 256a128.9 128.9 0 0 0 20-1.555V165z"
                  />
                </svg>
                Login with Facebook
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      content: "login", // Default to 'login' when the modal opens
      email: "",
      password: "",
      username: "",
      regEmail: "",
      regPassword: "",
      confirmPassword: "",
    };
  },
  methods: {
    closeModal() {
      this.$emit("close");
    },
    login() {
      // Handle login logic here
      alert(
        `Logging in with email: ${this.email} and password: ${this.password}`
      );
    },
    register() {
      // Handle register logic here
      if (this.regPassword !== this.confirmPassword) {
        alert("Passwords do not match!");
        return;
      }
      alert(
        `Registering with username: ${this.username}, email: ${this.regEmail}, and password: ${this.regPassword}`
      );
    },
  },
};
</script>

<style scoped>
/* Add your styles here */
</style>
