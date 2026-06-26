 <script setup>
import { ref } from 'vue'
 
const affichage = ref('0')
 
function ajouterChiffre(chiffre) {
  if (affichage.value === '0') {
    affichage.value = chiffre
  } else {
    affichage.value += chiffre
  }
}
 
function ajouterOperateur(op) {
  affichage.value += op
}
 
function calculer() {
  try {
    affichage.value = eval(affichage.value).toString()
  } catch {
    affichage.value = 'Erreur'
  }
}
 
function effacer() {
  affichage.value = '0'
}
</script>
 
<template>
 
 
 
  <div class="calculatrice">
    <div class="ecran">{{ affichage }}</div>
    <div class="boutons">
      <button @click="effacer">C</button>
      <button @click="ajouterOperateur('/')">/</button>
      <button @click="ajouterOperateur('*')">×</button>
      <button @click="ajouterOperateur('-')">-</button>
 
      <button @click="ajouterChiffre('7')">7</button>
      <button @click="ajouterChiffre('8')">8</button>
      <button @click="ajouterChiffre('9')">9</button>
      <button @click="ajouterOperateur('+')">+</button>
 
      <button @click="ajouterChiffre('4')">4</button>
      <button @click="ajouterChiffre('5')">5</button>
      <button @click="ajouterChiffre('6')">6</button>
      <button @click="calculer" class="egal">=</button>
 
      <button @click="ajouterChiffre('1')">1</button>
      <button @click="ajouterChiffre('2')">2</button>
      <button @click="ajouterChiffre('3')">3</button>
      <button @click="ajouterChiffre('0')" class="zero">0</button>
    </div>
  </div>
</template>
 
<style>
.calculatrice {
  width: 280px;
  margin:  auto;
  background: black;
  padding: 15px;
  border-radius: 10px;
}
.ecran {
  background: green;
  color: white;
  font-size:50px;
  text-align: right;
  padding: 15px;
  border-radius: 5px;
  margin-bottom: 19px;
}
.boutons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 8px;
}
button {
  padding: 15px;
  font-size: 29px;
  border: none;
  border-radius: 5px;
  background: right;
  color: white;
  cursor: pointer;
}
  
.egal {
  background: blue;
}
</style>