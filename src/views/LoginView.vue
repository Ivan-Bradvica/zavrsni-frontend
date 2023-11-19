<template>
    <section class="bg-gray-50 dark:bg-gray-900">
        <div class="flex flex-col items-center justify-center px-6 py-8 mx-auto md:h-screen lg:py-0"  >
             
            <div
                class="w-full bg-white rounded-lg shadow dark:border md:mt-0 sm:max-w-md xl:p-0 dark:bg-gray-800 dark:border-gray-700">
                <div class="p-6 space-y-4 md:space-y-6 sm:p-8">
                    <h1 class="text-xl font-bold leading-tight tracking-tight text-gray-900 md:text-2xl dark:text-white">
                        Sign in to your account
                    </h1>
                        <div>
                            <label for="email" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Your
                                email</label>
                            <input type="email" name="email" id="email" v-model="email"
                                class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                placeholder="name@company.com" required="">
                        </div>
                        <div>
                            <label for="password"
                                class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Password</label>
                            <input type="password" name="password" v-model="password" placeholder="••••••••"
                                class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                required="">
                        </div>
                        <div class="flex items-center justify-between">
                            
                            <a href="" id="password"
                                class="text-sm font-medium text-primary-600 hover:underline dark:text-primary-500">Forgot
                                password?</a>
                        </div>
                    <button class="login" @click="login()"
                        >Sign
                        In</button>
                    <p class="text-sm font-light text-gray-500 dark:text-gray-400">
                        Don’t have an account yet? <a href="/register"
                            class="font-medium text-primary-600 hover:underline dark:text-primary-500">
                            Sign up</a>
                    </p>
                    <p>Test@test.com</p>
                    <p>test123</p>
            </div>
        </div>
    </div>
</section>


</template>


<script>
import axios from "axios";

export default {
  data() {
    return {
      email: "",
      password: "",
      checked: false,
      registrationErrors: [],
      status: "",
    };
  },
  methods: {
    login() {
      axios
        .post(
          "/auth/login",
          {
            email: this.email,
            password: this.password,
          },
          {
            headers: {
              "Content-Type": "application/json",
            },
          }
        )
        .then((response) => {
          axios.defaults.headers.common["Authorization"] = "Bearer " + response.data.access_token;
          localStorage.setItem("token", JSON.stringify(response.data.access_token));
          this.toggleSuccessToast();
          this.$router.push("/")
        })
        .catch((error) => {
          if (error.response) {
            console.log(error.response.data.errors);
            this.registrationErrors = error.response.data.errors;
          } else if (error.request) {
            this.registrationErrors = ["The request was made but no response was received. Please try again later!"];
          }
          this.toggleErrorToast();
        });
    },

    // Success response message
    toggleSuccessToast() {
      this.$toast.add({
        severity: "success",
        summary: "Success Message",
        detail: "Logged in successfully!",
        life: 4000,
      });
    },

    // Error response message
    toggleErrorToast() {
      for (var i = 0; i < Object.keys(this.registrationErrors).length; i++) {
        this.$toast.add({
          severity: "error",
          summary: "Error Message",
          detail: Object.values(this.registrationErrors)[i],
          life: 4000,
        });
      }
    },
  },
};
</script>

<style>

.login{
    color: #fff; /* Tekst je bijel */
  background-color: #00bcd4; /* Pozadina je plava */
  width: 100%; /* Širina je 100% */
  padding: 0.5rem 0; /* Uklonili smo horizontalni padding */
  border-radius: 0.5rem;
  font-size: 1rem;
  font-weight: bold;
  text-align: center;
  border: none; /* Uklonili smo granicu */
  cursor: pointer;
}
.login:hover{
    background-color: #0E9F6E
    ;
  /* Dodajte stil za hover prema vašim preferencijama */    
}
</style>