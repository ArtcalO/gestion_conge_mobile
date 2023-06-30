<template>
  <ion-header>
    <ion-toolbar>
      <ion-buttons slot="start">
        <ion-button color="medium" @click="cancel">Cancel</ion-button>
      </ion-buttons>
      <ion-title>Modal</ion-title>
      <ion-buttons slot="end">
        <ion-button @click="confirm" :strong="true">Confirm</ion-button>
      </ion-buttons>
    </ion-toolbar>
  </ion-header>
  <ion-content class="ion-padding">
    <ion-item>
      <ion-input label-placement="stacked" label="Debut congé" v-model="conge_debut" type="date"></ion-input>
    </ion-item>
    <ion-item>
      <ion-input label-placement="stacked" label="Fin congé" v-model="conge_fin" placeholder="Your name" type="date"></ion-input>
    </ion-item>
    <br>
    <ion-button expand="block" @click="ajouterConge">Valider congé</ion-button>
  </ion-content>
</template>

<script>
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
    name: 'AddCongeModal',
    props:["idEmployeProps",],
    data(){
      return {
        conge_debut:null,
        conge_fin:null,
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
      ajouterConge(){
        let data = {
          idEmploye:this.idEmployeProps,
          conge_debut : this.conge_debut,
          conge_fin : this.conge_fin
        }

        return modalController.dismiss(data,'addCongeEmited')
      }
    },
  });
</script>