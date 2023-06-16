<template>
  <ion-app>
    <ion-router-outlet v-if="connected" />
    <LoginView v-else @loginEmited="connected=true"/>
  </ion-app>
</template>

<script>
import LoginView from "./components/LoginView.vue"
import { IonApp, IonRouterOutlet } from '@ionic/vue';
export default{
  components:{
    IonApp,
    IonRouterOutlet,
    LoginView
  },
  data(){
    return{
      connected:true
    }
  }
}
</script>
