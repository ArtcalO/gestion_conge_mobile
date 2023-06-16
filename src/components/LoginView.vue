<template>
    <ion-page>
        <ion-content class="ion-padding">
            <ion-item fill="outline">
                <ion-label position="floating">Username</ion-label>
                <ion-input type="text"></ion-input>
            </ion-item>
            <br>
            <ion-item fill="outline">
                <ion-label position="floating">Password</ion-label>
                <ion-input type="password"></ion-input>
            </ion-item>
            <br>
            <ion-button expand="block" @click="$emit('loginEmited')">Connexion</ion-button>
        </ion-content>
    </ion-page>
</template>

<script>
import {
    IonItem,
    IonLabel,
    IonInput,
    IonPage,
    IonContent,
    IonButton
} from "@ionic/vue";
export default {
  components:{
    IonLabel,
    IonItem,
    IonInput,
    IonPage,
    IonContent,
    IonButton
  },
  name: 'LoginView',

  data() {
    return {

    };
  },
};
</script>

<style lang="css" scoped>
#container {
  text-align: center;
  
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}
</style>
