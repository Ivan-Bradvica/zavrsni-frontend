<template>
  <nav class="bg-white dark:bg-gray-900  w-full z-20 top-0 left-0 border-b border-gray-200 dark:border-gray-600" id="nav">
    <div class="max-w-screen-xl flex flex-wrap items-center justify-between mx-auto p-4">
      <a href="/" class="flex items-center">
        <img src="demo/images/product/8207.jpg" alt="Image" style="width: 100px; height: 100px; object-fit:cover" />
        <span class="self-center text-2xl font-semibold whitespace-nowrap dark:text-white">Real Estate</span>
      </a>
      <div class="flex md:order-2">
        <button type="button" id="login"><a href="/login">Login</a> </button>
        <button type="button" id="register"><a href="/register" >Register</a></button>

        <button data-collapse-toggle="navbar-sticky" type="button"
          class="inline-flex items-center p-2 w-10 h-10 justify-center text-sm text-gray-500 rounded-lg md:hidden hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200 dark:text-gray-400 dark:hover:bg-gray-700 dark:focus:ring-gray-600"
          aria-controls="navbar-sticky" aria-expanded="false">
          <span class="sr-only">Open main menu</span>
          <svg class="w-5 h-5" aria-hidden="true" fill="none" viewBox="0 0 17 14">
            <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
              d="M1 1h15M1 7h15M1 13h15" />
          </svg>
        </button>
      </div>
      <div class="items-center justify-between hidden w-full md:flex md:w-auto md:order-1" id="navbar-sticky">
        <ul
          class="flex flex-col p-4 md:p-0 mt-4 font-medium border border-gray-100 rounded-lg bg-gray-50 md:flex-row md:space-x-8 md:mt-0 md:border-0 md:bg-white dark:bg-gray-800 md:dark:bg-gray-900 dark:border-gray-700">
           
           
         
          <li>
            <a href="/about"
              class="block py-2 pl-3 pr-4 text-gray-900 rounded hover:bg-gray-100 md:hover:bg-transparent md:hover:text-blue-700 md:p-0 md:dark:hover:text-blue-500 dark:text-white dark:hover:bg-gray-700 dark:hover:text-white md:dark:hover:bg-transparent dark:border-gray-700">O
              projektu</a>
          </li>

        </ul>
      </div>
    </div>
  </nav>
</template>
<style>
#login {
  color: #000;
  background-color: #fff;
  padding: 0.5rem 1rem;
  border-radius: 0.5rem;
  font-size: 1rem;
  font-weight: bold;
  text-align: center;
  border: 1px solid #000;
 
  margin-right: 1rem;
  
}

#login:hover {
  background-color: #d4f2e8;
}

#login:focus {
  outline: none;
  box-shadow: 0 0 0 4px rgba(0, 0, 255, 0.3);
}
#register{
  color: #ffffff;
    background-color: #4E5FBB;
    padding: 0.5rem 1rem;
    border-radius: 0.5rem;
    font-weight: bold;
    font-size: 1rem;
    text-align: center;
    cursor: pointer;

}
#register:hover {
    background-color: rgb(75, 66, 196);
    /* Dodajte stil za hover prema vašim preferencijama */
}
#nav{
  height: 150px;
}
</style>

<script setup>
 </script>