<template>
  <div id="app">
    <header class="p-2 text-black/60">
      <nav class="text-center">
        <router-link to="/">Home</router-link>
      </nav>

      <h1 class="text-2xl text-center my-5">
        X Blog
      </h1>
    </header>

    <main class="w-full md:w-2/3 mx-auto">
      <router-view/>
    </main>
  </div>
</template>
