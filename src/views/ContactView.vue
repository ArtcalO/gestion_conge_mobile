<template>
    <ion-page>
        <h1>Contact Page</h1>
        <ion-button @click="ugurura">Open Action Sheet</ion-button>
        <ion-button @click="ugururaAlert">Holla</ion-button>
    </ion-page>
</template>

<script>
import {IonPage, IonButton, actionSheetController,alertController } from "@ionic/vue"

export default {

  name: 'ContactView',
  components:{
    IonPage,
    IonButton
  },
  data() {
    return {

    };
  },
  methods:{
    async ugururaAlert(){
       const alert = await alertController.create({
          header: 'Alert',
          subHeader: 'Important message',
          message: 'This is an alert!',
          buttons: ['OK'],
        });

        await alert.present()
    },
    async ugurura(){
        const actionSheet = await actionSheetController.create({
          header: 'Actions',
          buttons: [
            {
              text: 'Delete',
              role: 'destructive',
              data: {
                action: 'delete',
              },
            },
            {
              text: 'Share',
              data: {
                action: 'share',
              },
            },
            {
              text: 'Cancel',
              role: 'cancel',
              data: {
                action: 'cancel',
              },
            },
          ],
        });
        console.log(actionSheet)
        await actionSheet.present();
    }
  }
};
</script>

<style lang="css" scoped>
</style>
