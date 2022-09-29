<template>
  <nav>
    <h4>Lucas Moramarco MMI2 A2</h4>
    <h4 class="text-xl">
      <Bars3Icon class="inline-block h-5 w-5 text-blue-500" />
      menu (dans <code class="font-mono">/src/App.vue</code>)
    </h4>
    <ul>
      <li>
        <router-link class="text-red-600 underline" to="/">
          Accueil
        </router-link>
      </li>
      <li>
        <router-link class="text-red-600 underline" to="/simple">
          Simple
        </router-link>
      </li>
      <li>
        <router-link class="text-red-600 underline" to="/liste">
          Liste
        </router-link>
      </li>
      <li>
        <router-link class="text-red-600 underline" to="/liste-fetch">
          Liste fetch
        </router-link>
      </li>
      <li>
        <router-link class="text-red-600 underline" to="/edit/new">
          New
        </router-link>
      </li>
      <li>
        <router-link class="text-red-600 underline" to="/liste-supabase">
          Liste supabase
        </router-link>
      </li>
      <li>
        <router-link class="text-red-600 underline" to="/login">
          <h2>Se connecter</h2>
        </router-link>
      </li>
      <router-link class="text-red-600 underline" to="/edit/id">
            <h2>Page ID</h2>
        </router-link>
    </ul>
  </nav>

  <!-- Affiche les pages -->
  <Suspense>
     <router-view class="m-2 border-2 p-2" />
     </Suspense>
</template>

<script setup lang="ts">
import { Bars3Icon } from "@heroicons/vue/20/solid";
</script>
