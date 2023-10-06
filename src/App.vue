<script setup lang="ts">
import { ref, onMounted } from 'vue';

let array = ref<Number[]>([])
let numeroCasa = ref<Number>(49);
let numeroParede = ref<Number[]>([])
let persoonagem = 2;

for (let index = 0; index < 60; index++) {
  let casa: Number = index + 1;
  array.value.push(casa);
  if (casa != 1 && casa != 2 && casa != 3 && casa != 4 && casa != 5 && casa != 6 && casa != 7 && casa != 8 && casa != 9 && casa != 10 && casa != 11 && casa != 12 && casa != 13 && casa != 25 && casa != 37 && casa != 49) {
    numeroParede.value.push(casa);
    console.log(numeroParede);
  }

}

function mudaCasa(): void {
  if (event.key == 's') {

    if (numeroCasa.value + 12 <= 60) {
      numeroCasa.value += 12
    }

  }
  if (event.key == 'w') {

    if (numeroCasa.value - 12 > 0) {
      numeroCasa.value -= 12
    }

  }
  if (event.key == 'd') {
    if (numeroCasa.value % 12 == 0) {

    } else {
      numeroCasa.value += 1
    }
  }

  if (event.key == 'a') {
    if ((numeroCasa.value + 11) % 12 == 0) {
    } else {
      numeroCasa.value -= 1
    }
  }
}
onMounted(() => {
  window.addEventListener('keypress', mudaCasa);
})

</script>

<template>
  <section>
    <div class="grid-full grid grid-cols-12 gap-4">
      <div class="box" v-for="numero of array">
          <div v-if="numeroCasa == numero">
            {{ persoonagem }}
          </div>
        <div  v-for="numeroParedeA of numeroParede">
        <div class="bg-slate-600 parede" v-if="numeroParedeA == numero">
          {{ numeroParedeA }}
        </div>
      </div>

    </div>
    </div>
  </section>
</template>

<style scoped>
.grid-full {
  @apply w-screen h-screen;
}

.box {
  @apply border-sky-500 border-2 w-full h-full;
}

.parede {
  width: 100%;
  height: 100%;
}
</style>
