<script setup lang="ts">
import { ref, onMounted } from 'vue';

let array = ref<Number[]>([])
let numeroCasa = ref<Number>(193);
let numeroParede = ref<Number[]>([])
let persoonagem = "👲";
let boolean;

for (let index = 0; index < 240; index++) {
  let casa: Number = index + 1;
  array.value.push(casa);
  if(numeroCasa.value!=48){
    if (casa !=193 && casa!=194 && casa!=170 && casa!=146 && casa!=122 
    && casa!=123 && casa!=99 && casa!=75 && casa!=124 && casa!=125 && casa!=126 
    && casa!=101 && casa!=77 && casa!=53 && casa!=29 && casa!=28 && casa!=54 
    && casa!=150 && casa!=174 && casa!=198 && casa!=173 && casa!=172 && casa!=175 
    && casa!=127 && casa!=128 && casa!=104 && casa!=80 && casa!=56 && casa!=57 
    && casa!=58 && casa!=34 && casa!=82 && casa!=106 && casa!=130 && casa!=131
    && casa!=154 && casa!=178 && casa!=202 && casa!=203 && casa!=204 && casa!=205 && casa!=206
    && casa!=182 && casa!=207 && casa!=208 && casa!=209 && casa!=210 && casa!=211 && casa!=212
    && casa!=188 && casa!=189 && casa!=190 && casa!=214 && casa!=166 && casa!=142
    && casa!=143 && casa!=164 && casa!=140 && casa!=139 && casa!=138 && casa!=137 && casa!=136 
    && casa!=135 && casa!=134 && casa!=133 && casa!=109 && casa!=85 && casa!=61 && casa!=62 && casa!=38 && casa!=63
    && casa!=87 && casa!=64 && casa!=65 && casa!=89 && casa!=90 && casa!=91 && casa!=67
    && casa!=43 && casa!=44 && casa!=45&& casa!=69&& casa!=93 && casa!=94 && casa!=95 && casa!=71 && casa!=47 && casa!=48  ) {
      numeroParede.value.push(casa);
    }
  }
}
function final(){
    numeroParede = ref<Number[]>([]);
  numeroCasa = ref<Number>(97);
  for (let index = 0; index < 240; index++) {
  let casa: Number = index + 1;
  if(casa !=97 && casa !=98 && casa !=99 && casa !=100 && casa !=101 && casa !=102 &&casa !=103 && casa !=104 && casa !=105 && casa !=106 && casa !=107 && casa !=108 && casa !=109 && casa !=110 && casa !=111 && casa !=112 && casa !=113 && casa !=114 
    && casa !=115 && casa !=116 && casa !=117 && casa !=118 && casa !=119 && casa !=120){
      numeroParede.value.push(casa);
    } 
  }
  boolean = true;
}
function recomecar(){
  location.reload();
}
function verificacaoParede(numero):boolean{

  for (let element of numeroParede.value) {    
    if(element==numero){
      return true
    }
  }
  return false
}

function mudaCasa(): void {
  if (event.key == 's' || event.key == 'S') {

    if (numeroCasa.value + 24 <= 240 && !verificacaoParede(numeroCasa.value+24)) {
      numeroCasa.value += 24
    }

  }
  if (event.key == 'w'|| event.key == 'W') {

    if (numeroCasa.value - 24 > 0 && !verificacaoParede(numeroCasa.value-24)) {
      numeroCasa.value -= 24
    }

  }
  if (event.key == 'd' || event.key == 'D') {
    if (numeroCasa.value % 24 == 0) {
    } else if(!verificacaoParede(numeroCasa.value+1)) {
      numeroCasa.value += 1
    }
  }
  
  if (event.key == 'a'|| event.key == 'A') {
    if ((numeroCasa.value + 23) % 24 == 0) {
    } else if(!verificacaoParede(numeroCasa.value-1)){
      numeroCasa.value -= 1
    }
  }
}
onMounted(() => {
  window.addEventListener('keypress', mudaCasa);
})

</script>

<template>
  <section class=" bg-black h-screen w-screen flex justify-center items-center">

    <div class="w-full h-full" v-if="numeroCasa==48" :V-bind=final()></div> 
    <div v-if="boolean" class="absolute mb-64  text-6xl"   >FINAL</div>
      <button v-if="boolean" class="absolute mt-72 bg-black text-white p-2" @click = recomecar()> Recomeçar </button>
    
    <div class="grid">
      <div class="box " v-for="numero of array">
          <div class="w-full h-full flex justify-center items-center" v-if="numeroCasa == numero">
            {{ persoonagem }}
          </div>
          <div class="bg-gray-500 w-full h-full flex justify-center items-center" v-if="numeroParede.includes(numero)">
              #
          </div>
          <div class="w-full h-full flex justify-center items-center" v-if="numero == 48">
            E
          </div>
          <div v-if="">  <div>
        </div>
      </div>
  </section>
</template>

<style scoped>
.grid-full {
  @apply w-screen h-screen;
}

.box {
  background:white;
}

.parede {
  width: 100%;
  height: 100%;
}
.grid{

  display:grid;
  grid-template-columns:repeat(24, 50px);
  grid-template-rows:repeat(10, 50px);
}
</style>
