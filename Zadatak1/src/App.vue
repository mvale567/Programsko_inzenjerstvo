<script setup>
import { ref } from "vue";

const filmovi = ref([
  {
    id: 1,
    naziv: "Naslov Filma "
  }, {
    id: 2,
    naziv: "Naslov Filma "
  },
  {
    id: 3,
    naziv: "Naslov Filma "
  }
])

</script>

<template>
  <div class="min-h-screen bg-gradient-to-br from-emerald-950 to-indigo-950 text-teal-100 flex flex-col justify-center">

    <h1 class="text-[60px] mb-5 text-center mx-auto">
      Pozdrav, ja sam <span class="text-cyan-400">Marko Valečić</span>
    </h1>

    <hr class="w-[1024px] border-2 opacity-75 rounded-full mx-auto" />

    <div class="mt-8 max-w-[1024px] mx-auto">
      <p class="text-[24px] text-teal-100/75">Moji omiljeni filmovi</p>

      <ul class="flex justify-center gap-6 mt-6">
        <li v-for="film in filmovi" class="flex flex-col items-center">
          <div
            class="w-[320px] h-[480px] bg-gray-200 rounded-md flex items-center justify-center text-gray-500 text-5xl font-bold ">
            Poster
          </div>
          <p class="text-[24px] mt-2 text-white">{{ film.naziv }}</p>
        </li>
      </ul>
    </div>


  </div>
</template>

<style scoped></style>
