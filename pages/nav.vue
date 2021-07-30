<template>
  <div>
    <ul class="bg-gray-300">
      <i>
        <nuxt-link to="/nav/about">About</nuxt-link>
        <nuxt-link to="/nav/contact">Contact</nuxt-link>
      </i>
    </ul>
    <div class="bg-gray-500">
      <nuxt-child />
    </div>
  </div>
</template>
