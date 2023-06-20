<template>
  <ion-header>
    <ion-toolbar color="primary">
      <ion-buttons slot="start">
        <ion-button color="medium" @click="cancel">Cancel</ion-button>
      </ion-buttons>
      <ion-title>Modifier employé</ion-title>
      <ion-buttons slot="end">
        <ion-button @click="confirm" :strong="true">Confirm</ion-button>
      </ion-buttons>
    </ion-toolbar>
  </ion-header>
  <ion-content class="ion-padding">
    <ion-item>
      <ion-input label-placement="stacked" label="Nom Employé" v-model="employeObj.nom" placeholder="Your name"></ion-input>
    </ion-item>
    <ion-item>
      <ion-input label-placement="stacked" label="Prenom" v-model="employeObj.prenom" placeholder="Your name"></ion-input>
    </ion-item>
    <ion-item>
      <ion-input label-placement="stacked" label="Age" v-model="employeObj.age" placeholder="Your name"></ion-input>
    </ion-item>
    <ion-button expand="block">Modifier</ion-button>
  </ion-content>
</template>

<script >
  import {
    IonContent,
    IonHeader,
    IonTitle,
    IonToolbar,
    IonButtons,
    IonButton,
    IonItem,
    IonInput,
    modalController,
  } from '@ionic/vue';
  import { defineComponent } from 'vue';

  export default defineComponent({
    name: 'ModifierEmploye',
    props:["employe"],
    data(){
      return {
        employeObj:this.employe
      }
    },
    components: { IonContent, IonHeader, IonTitle, IonToolbar, IonButtons, IonButton, IonItem, IonInput },
    methods: {
      cancel() {
        return modalController.dismiss(null, 'cancel');
      },
      confirm() {
        return modalController.dismiss(this.name, 'confirm');
      },
    },
  });
</script>