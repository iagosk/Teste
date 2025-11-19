<script setup lang="ts">
import { ref, computed } from "vue";

// Armazena temperatura em graus celsius;
let temperaturaC = ref<number>(0);
// Armazena temperatura em graus Fahrenheit ;
let temperaturaF = ref<number>(0);
// Armazena temperatura em graus Kelvin ;
let temperaturaK = ref<number>(0);

const conversaoF = computed(() => {
  temperaturaF.value = (temperaturaC.value * 9/5) + 32;
});

const conversaoK = computed(() => {
  temperaturaK.value = temperaturaC.value + 273.15;
});

</script>

<template>
  <h1>Conversor de Temperatura</h1>
  <br />
  <br />
  <form action="">
    <p>
      <input type="number" v-model="temperaturaC" name="temperatura" id="temperatura" class="inputForm" placeholder="Temperatura em graus Celsius:" required>
    </p>
  </form>
  <br />
  {{ conversaoF }}
  {{ conversaoK  }}
  <p>
    <h2>Temperatura em Graus Celsius: {{ temperaturaC }}</h2>
    <br />
    <h2 class="vermelha">Temperatura em Graus Fahrenheit: {{ temperaturaF }}</h2>
    <br />
    <h2 class="azul">Temperatura em Graus Kelvin: {{ temperaturaK }}</h2>
  </p>
  <br />
  <h2>Mensagem:</h2>
  <br />
  <p v-if="temperaturaC < 0">Água estaria congelada nessa temperatura.</p>
  <p v-else-if="temperaturaC >=0 && temperaturaC < 100">Temperatura comum no dia a dia.</p>
  <p v-else="temperaturaC >= 100">Água entraria em ebulição nessa temperatura.</p>
</template>

<style scoped>
  .inputForm {
    border-radius: 8px;
    padding: 8px;
    font-size: 1.1rem;
    border: 4px solid rgb(36, 1, 211);
  }

  .vermelha {
    color: red;
  }

  .azul {
    color: rgb(34, 34, 255);
  }
</style>
