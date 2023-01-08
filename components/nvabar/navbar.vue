<template>
  <div class="sticky top-0 z-50 navbar shadow bg-neutral bg-base-100">
  <div class="navbar-start">
    <div class="dropdown">
      <label tabindex="0" class="btn btn-ghost lg:hidden">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h8m-8 6h16" /></svg>
      </label>
      <ul tabindex="0" class="menu menu-compact dropdown-content mt-3 p-2 shadow bg-base-100 rounded-box w-52">
        <li>
          <nuxt-link to="/">Home</nuxt-link>


          <!-- <nuxt-link
          v-for="(route, index) in routes"
          :key="index"
          exact
          :to="localePath(route.path)"
          class="capitalize block h-16 leading-[4rem] border-b-4 border-transparent hover:text-red-700 hover:border-current"
          >{{ $t(route.label) }}</nuxt-link
        > -->
        </li>
        <li><nuxt-link to="/blog">Lesson Posts</nuxt-link></li>
        <li><nuxt-link to="/about-us">About</nuxt-link></li>
      </ul>
    </div>
    <nuxt-link to="/">
      <img src="/circle.png" class="w-12"/>
    </nuxt-link>
    <span class="p-4">Learn Tech</span>
    <!-- <nuxt-link exact :to="localePath('index')">
      <img src="/circle.png" class="w-8" />
    </nuxt-link> -->
  </div>
  <div class="navbar-center hidden lg:flex">
    <ul class="menu menu-horizontal px-1">
      <li>
        <nuxt-link to="/">ទំព័រដើម</nuxt-link>
        <!-- <nuxt-link
          v-for="(route, index) in routes"
          :key="index"
          exact
          :to="localePath(route.path)"
          class="capitalize block h-16 leading-[4rem] border-b-4 border-transparent hover:text-red-700 hover:border-current"
          >{{ $t(route.label) }}</nuxt-link
        > -->
      </li>
      <li><nuxt-link to="/blog">Lesson Posts</nuxt-link></li>
      <li><nuxt-link to="/about-us">About</nuxt-link></li>
    </ul>
  </div>
</div>
</template>

<script>
  // import { routes } from "static/js/routes"
  // export default {
  //   data() {
  //   return {
  //     routes: routes,
  //   };
  // },
  // }
</script>

<style scoped>

</style>
