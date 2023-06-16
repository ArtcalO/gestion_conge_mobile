<template>
  <ion-page>
    <ion-header :translucent="true" >
      <ion-toolbar color="primary">
        <ion-title>Liste Employées</ion-title>
        <ion-icon :icon="person" size="large" slot="end"></ion-icon>
      </ion-toolbar>
    </ion-header>

    <ion-content :fullscreen="true" class="ion-padding">
      <ion-list>
        <ion-item v-for="i in 20" :key="i" >
          <ion-avatar slot="start" ><img src="../assets/logo.jpg"></ion-avatar>
          <ion-label>
            <h2>Employe num : {{i}}</h2>
            <p>Bonjour</p>
          </ion-label>
          <ion-button slot="end" color="primary">
            <ion-icon :icon="add"></ion-icon>
          Congé</ion-button>
        </ion-item>
      </ion-list>
    </ion-content>
  </ion-page>
</template>

<script>
import {
  IonContent,
  IonHeader,
  IonPage,
  IonTitle,
  IonToolbar,
  IonIcon,
  IonList,
  IonItem,
  IonAvatar,
  IonLabel,
  IonButton,

} from '@ionic/vue';

import {person, add} from "ionicons/icons"
export default{
  data(){
    return {
      person,
      add,
    }
  },
  components:{
    IonContent,IonHeader,IonIcon,IonButton,
    IonPage, IonTitle, IonToolbar,
    IonList,IonItem, IonAvatar,IonLabel
  }
}
</script>

<style scoped>
#container {
  text-align: center;
  
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;
  
  color: #8c8c8c;
  
  margin: 0;
}

#container a {
  text-decoration: none;
}
</style>
