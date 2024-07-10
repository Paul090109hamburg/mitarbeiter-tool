<script setup lang="ts">

import {ref} from "vue";

let idCounter = 0;

type Mitarbeiter = {
  id: string,
  name: string,
  rolle: string,
}

type Review = {
  id: string,
  text: string,
  mitarbeiter: string,
  vorgesetzen: string,
}

function onClickOpenButton() {
  showCreationForm.value = true;
}

function onClickOpenButton2() {
  showReviewForm.value = true;
}

const mitarbeiterListe = ref<Mitarbeiter[]>([]);
const reviewListe = ref<Review[]>([]);

const neuerName = ref('');
const neueRolle = ref('');
const neuerReviewText = ref('');
const mitarbeiter1 = ref('');
const mitarbeiter2 = ref('');



const showCreationForm = ref(false);
const showReviewForm = ref(false);

function  onClickCreateButton() {

  idCounter = idCounter + 1;

  mitarbeiterListe.value.push(
      {
        id: idCounter.toString(),
        name: neuerName.value,
        rolle: neueRolle.value
      }
  );

  neuerName.value = '';
  neueRolle.value = '';
  showCreationForm.value = false;
}


function  onClickReviewButton() {

  idCounter = idCounter + 1;

  reviewListe.value.push(
      {
        id: idCounter.toString(),
        text: neuerReviewText.value,
        mitarbeiter: mitarbeiter1.value,
        vorgesetzen: mitarbeiter2.value,
      }
  );

}




</script>

<template>
  <main>

    <h1 class="headline">mitarbeiter-tool</h1>

    <button class="button-1" @click="onClickOpenButton">mitarbeiter erstellen</button>
    <button class="button-2" @click="onClickOpenButton2">Gespräch beginnen</button>

    <div v-if="showCreationForm" class="form-box">
      <input class="Name-von-Mitarbeiter" v-model="neuerName" placeholder="Name vom Mitarbeiter"/>
      <input class="rolle" v-model="neueRolle" placeholder="rolle"/>
      <button class="jetzt-mitarbeiter-anlegen" @click="onClickCreateButton">Jetzt Mitarbeiter anlegen</button>
    </div>

    <div class="form-box" v-if="showReviewForm">
      <textarea class="zsm-v-talk" v-model="neuerReviewText" placeholder="Zusammenfassung vom Gespräch"/>
      <div class="select-kontainer">
        <div>
          <select class="select-1" v-model="mitarbeiter1">
            <option v-for="mitarbeiter in mitarbeiterListe" :value="mitarbeiter.name">{{mitarbeiter.name}}</option>
          </select>
        </div>

        <div>
          <select class="select-2" v-model="mitarbeiter2">
            <option v-for="mitarbeiter in mitarbeiterListe" :value="mitarbeiter.name">{{mitarbeiter.name}}</option>
          </select>
        </div>
      </div>

      <div class= "review-button-box" >
        <button @click="onClickReviewButton">Review speichern</button>
      </div>
    </div>

    <div class="kontainer-listen"> <div>
      <h2 class="anzahl-der-mitarbeiter">Anzahl der Mitarbeiter: {{mitarbeiterListe.length}}</h2>
      <ul>
        <li v-for="mitarbeiter in mitarbeiterListe">{{ mitarbeiter.name }} ({{mitarbeiter.rolle}})</li>
      </ul>
    </div>

      <div>
        <h2 class="anzahl-der-mitarbeiter">Anzahl der Gespräche: {{reviewListe.length}}</h2>

        <ul>
          <li v-for="review in reviewListe">{{ review.text }} {{review.mitarbeiter}} {{review.vorgesetzen}}</li>
        </ul>
      </div>
    </div>
    
  </main>
</template>

<style>

.headline {
  color:cadetblue;
  font-size:30px;
  margin: 8px auto;
  width: 400px;
  text-align: center;
  border-color: cadetblue;
  border-style: solid;
  border-width:2px;
}
.anzahl-der-mitarbeiter{
  color: cornflowerblue;
font-size: 17px;


}
.jetzt-mitarbeiter-anlegen{
  background-color:wheat;
  border-color: white;
  margin-right: 25px;
  color:grey;
}

.select-1{
  min-width: 200px;
}

.select-2{
  min-width: 200px;

}
.zsm-v-talk {
  min-width: 100%;
}
.button-1{
  background-color:lightblue;
  border-color: white;
  color: grey;
}

.button-2{
  background-color: lightblue;
  border-color: white;
  color: grey;
}
.Name-von-Mitarbeiter{
  background-color: wheat;
  border-color:white;
  margin-right: 19px
}
.review-button-box{
  text-align: right;
}
.rolle{
  background-color:wheat;
  border-color: white;
  margin-left: 19px
}

.kontainer-listen{
  display: flex;
  flex-direction: column;
  gap: 20px;
  margin-top: 10px;
  justify-content: space-between;
}
.select-kontainer{
  display: flex;
  gap: 10px;
}

.kontainer-listen > div {
  padding: 20px;
  background-color: lightsteelblue;
  border-color: white;
  border-style: solid;
  border-width: 1px;
  border-radius: 5px;
}

.form-box {
  margin-top: 8px;
  border-color: #ff0000;
  border-style: solid;
  border-width: 2px;
  padding: 16px;
  width: 600px;
margin-bottom: 20px;
}

@media screen and (min-width:600px) {
  .form-box {
    border-color: lightblue;
    border-radius: 20px;
  }

  .kontainer-listen{
    flex-direction: row;
  }
}


</style>
