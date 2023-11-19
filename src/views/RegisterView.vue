<!--<template>
    <div class="container ">
        <section class="bg-gray-50 dark:bg-gray-900 mt-10">
            <div class="flex flex-col items-center justify-center px-6 py-8 mx-auto md:h-screen lg:py-0">

                <div
                    class="w-full bg-white rounded-lg shadow dark:border md:mt-0 sm:max-w-md xl:p-0 dark:bg-gray-800 dark:border-gray-700">
                    <div class="p-6 space-y-4 md:space-y-6 sm:p-8">
                        <h1
                            class="text-xl font-bold leading-tight tracking-tight text-gray-900 md:text-2xl dark:text-white">
                            Create an account
                        </h1>
                        <form class="space-y-4 md:space-y-6" action="#">


                            <div>
                                <label for="first_name"
                                    class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">First Name</label>
                                <input type="text" name="ime"  placeholder="First Name" v-model="first_name"
                                    class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                    required="">
                            </div>
                            <div>
                                <label for="last_name"
                                    class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Last Name</label>
                                <input type="text" name="prezime"  placeholder="Last Name" v-model="last_name"
                                    class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                    required="">
                            </div>
                            <div>
                                <label for="username"
                                    class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Username</label>
                                <input type="text" name="korisnicko"  placeholder="username" v-model="username"
                                    class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                    required="">
                            </div>

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
                                <input type="password" name="password" id="password" placeholder="••••••••" v-model="password"
                                    class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                    required="">
                            </div>



                            <button class="register">Create an account</button>
                            <p class="text-sm font-light text-gray-500 dark:text-gray-400">
                                Already have an account? <a href="/login"
                                    class="font-medium text-primary-600 hover:underline dark:text-primary-500">Login
                                    here</a>
                            </p>
                        </form>
                    </div>
                </div>
            </div>
        </section>
    </div>
</template>

<script >

// initialize components based on data attribute selectors


import axios from "axios";
export default {
    data() {
        return {
            email: "",
            password: "",

            first_name: "",
            last_name: "",
            username: "",
        };
    },
    methods: {
        register() {
            axios
                .post(
                    "/auth/register",
                    {
                        first_name: this.name,
                        last_name: this.surname,
                        username: this.username,
                        email: this.email,
                        password_confirmation: this.confirmed_password,


                    },
                    {
                        headers: {
                            "Content-Type": "application/json",
                        },
                    }
                )
                .then((response) => {
                    console.log(response.data);
                    axios.defaults.headers.common["Authorization"] = "Bearer " + response.data.access_token;
                    localStorage.setItem("token", JSON.stringify(response.data.access_token));
                    this.toggleSuccessToast();
                    setTimeout(() => this.$router.push("/"), 1500);
                })
                .catch((error) => {
                    if (error.response) {
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
                detail: "User created successfully! Redirecting yout to the home page...",
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








}
</script>

<style>
.register {
    color: #fff;
    /* Tekst je bijel */
    background-color: #00bcd4;
    /* Pozadina je plava */
    width: 100%;
    /* Širina je 100% */
    padding: 0.5rem 0;
    /* Uklonili smo horizontalni padding */
    border-radius: 0.5rem;
    font-size: 1rem;
    font-weight: bold;
    text-align: center;
    border: none;
    /* Uklonili smo granicu */
    cursor: pointer;
}
</style>
-->

<template>
    <div class="container">
        <section class="bg-gray-50 dark:bg-gray-900 mt-10">
            <div class="flex flex-col items-center justify-center px-6 py-8 mx-auto md:h-screen lg:py-0">
                <div
                    class="w-full bg-white rounded-lg shadow dark:border md:mt-0 sm:max-w-md xl:p-0 dark:bg-gray-800 dark:border-gray-700">
                    <div class="p-6 space-y-4 md:space-y-6 sm:p-8">
                        <h1
                            class="text-xl font-bold leading-tight tracking-tight text-gray-900 md:text-2xl dark:text-white">
                            Create an account
                        </h1>
                        <form class="space-y-4 md:space-y-6" @submit.prevent="register">

                            <div>
                                <label for="email" class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Your
                                    email</label>
                                <input type="email" name="email" id="email" v-model="email"
                                    class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                    placeholder="name@company.com" required>
                            </div>

                            <div>
                                <label for="first_name"
                                    class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">First Name</label>
                                <input type="text" name="ime" placeholder="First Name" v-model="first_name"
                                    class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                    required>
                            </div>

                            <div>
                                <label for="password"
                                    class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Password</label>
                                <input type="password" name="password" id="password" placeholder="••••••••"
                                    v-model="password"
                                    class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                    required>
                            </div>
                            <div>
                                <label for="password confirm"
                                    class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Password</label>
                                <input type="password" name="password" id="password confirm" placeholder="••••••••"
                                    v-model="confirmed_password"
                                    class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                    required>
                            </div>


                            <div>
                                <label for="last_name"
                                    class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Last Name</label>
                                <input type="text" name="prezime" placeholder="Last Name" v-model="last_name"
                                    class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                    required>
                            </div>
                            <div>
                                <label for="username"
                                    class="block mb-2 text-sm font-medium text-gray-900 dark:text-white">Username</label>
                                <input type="text" name="korisnicko" placeholder="Username" v-model="username"
                                    class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                    required>
                            </div>



                            <button class="register" @click="register()">Register
                            </button>
                            <p class="text-sm font-light text-gray-500 dark:text-gray-400">
                                Already have an account? <a href="/login"
                                    class="font-medium text-primary-600 hover:underline dark:text-primary-500">Login
                                    here</a>
                            </p>
                        </form>
                    </div>
                </div>
            </div>
        </section>
    </div>
</template>
  
<script>
import axios from "axios";

export default {
    data() {
        return {
            email: "",
            password: "",
            first_name: "",
            last_name: "",
            username: "",
            confirmed_password: "",

        };
    },
    methods: {
        register() {
            axios
                .post(
                    "/auth/register",
                    {
                        first_name: this.first_name,
                        last_name: this.last_name,
                        username: this.username,
                        email: this.email,
                        password: this.password,
                        password_confirmation: this.confirmed_password,
                    },
                    {
                        headers: {
                            "Content-Type": "application/json",
                        },
                    }
                )
                .then((response) => {
                    console.log(response.data);
                    axios.defaults.headers.common["Authorization"] = "Bearer " + response.data.access_token;
                    localStorage.setItem("token", JSON.stringify(response.data.access_token));
                    this.toggleSuccessToast();
                    setTimeout(() => this.$router.push("/"), 1500);
                })
                .catch((error) => {
                    if (error.response) {
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
                detail: "User created successfully! Redirecting you to the home page...",
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
.register {
    color: #fff;
    /* Tekst je bijel */
    background-color: #00bcd4;
    /* Pozadina je plava */
    width: 100%;
    /* Širina je 100% */
    padding: 0.5rem 0;
    /* Uklonili smo horizontalni padding */
    border-radius: 0.5rem;
    font-size: 1rem;
    font-weight: bold;
    text-align: center;
    border: none;
    /* Uklonili smo granicu */
    cursor: pointer;
}

.register:hover {
    background-color: #0E9F6E;
    /* Dodajte stil za hover prema vašim preferencijama */
}
</style>
  