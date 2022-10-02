<template>
  <nav>
    <h4 class="text-center p-4 font-semibold text-teal-800">Lucas Moramarco MMI2 A2</h4>

    <div class=" lg:hidden flex items-center">
      <button v-on:click="menuNav = !menuNav " class=" py-6 px-3 ">
        <Bars3Icon class="h-10 w-10 text-teal-800" :class="{hidden: !menuNav}" />
      </button>
    </div>

  <!-- Menu visible pour les formats allant de xs à lg  -->
  <div class="flex lg:hidden bg-teal-200" :class="{hidden: menuNav }">
      <button v-if="!menuNav" v-on:click="menuNav = !menuNav" class=" py-6 px-3 ">
        <XMarkIcon class="h-10 w-10 text-teal-800" />
      </button>
    <ul class="text-teal-900   mx-auto">
      <li>
        <router-link class="hover:text-orange-700  underline" to="/">
          Accueil
        </router-link>
      </li>
      <li>
        <router-link class="hover:text-orange-700 underline" to="/simple">
          Simple
        </router-link>
      </li>
      <li>
        <router-link class="hover:text-orange-700 underline" to="/liste">
          Liste
        </router-link>
      </li>
      <li>
        <router-link class="hover:text-orange-700 underline" to="/liste-fetch">
          Liste fetch
        </router-link>
      </li>
      <li>
        <router-link class="hover:text-orange-700 underline" to="/edit/new">
          New
        </router-link>
      </li>
      <li>
        <router-link class="hover:text-orange-700 underline" to="/liste-supabase">
          Liste supabase
        </router-link>
      </li>
      <li>
        <router-link class="hover:text-orange-700 underline" to="/login">
          <h2>Se connecter</h2>
        </router-link>
      </li>
      <li>
          <router-link class="hover:text-orange-700 underline" to="/quartier">
            <h2>Index quartier</h2>
          </router-link>
        </li>
      <li>
        <router-link class="hover:text-orange-700 underline" to="/quartier/new">
          <h2>New quartier</h2>
        </router-link>
      </li>
      
    </ul>
  </div>

  <!-- Menu sans îcones pour les formats >lg -->
  <div class="hidden lg:flex justify-center bg-teal-200">
    <ul>
      <li>
        <router-link class="hover:text-orange-700 underline" to="/">
          Accueil
        </router-link>
      </li>
      <li>
        <router-link class="hover:text-orange-700 underline" to="/simple">
          Simple
        </router-link>
      </li>
      <li>
        <router-link class="hover:text-orange-700 underline" to="/liste">
          Liste
        </router-link>
      </li>
      <li>
        <router-link class="hover:text-orange-700 underline" to="/liste-fetch">
          Liste fetch
        </router-link>
      </li>
      <li>
        <router-link class="hover:text-orange-700 underline" to="/edit/new">
          New
        </router-link>
      </li>
      <li>
        <router-link class="hover:text-orange-700 underline" to="/liste-supabase">
          Liste supabase
        </router-link>
      </li>
      <li>
        <router-link class="hover:text-orange-700 underline" to="/login">
          <h2>Se connecter</h2>
        </router-link>
      </li>
      
      <li>
        <router-link class="hover:text-orange-700 underline" to="/quartier">
          <h2>Index quartier</h2>
        </router-link>
      </li>
      <li>
        <router-link class="hover:text-orange-700 underline" to="/quartier/new">
          <h2>New quartier</h2>
        </router-link>
      </li>
    </ul>
  </div>
  </nav>

  <!-- Affiche les pages -->
  <Suspense>
     <router-view class="m-2 border-2 p-2" />
     </Suspense>
</template>

<script setup lang="ts">
import { Bars3Icon, XMarkIcon } from '@heroicons/vue/20/solid';
import { ref } from 'vue';
const menuNav = ref(true);
</script>
