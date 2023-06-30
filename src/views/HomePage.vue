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
        <ion-item v-for="employe in listeEmployes" :key="employe.id" >
          <ion-label>
            <h2>{{employe.nom}} {{employe.prenom}}</h2>
            <p>{{employe.genre}}</p>
          </ion-label>

          <ion-button @click="ajouterConge(employe.id)" slot="end" color="primary">
            <ion-icon :icon="add"></ion-icon>
          </ion-button>
          <ion-button @click="modifierEmploye" slot="end" color="warning">
            <ion-icon :icon="pencil"></ion-icon>
          </ion-button>
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
  IonLabel,
  IonButton,
  modalController,

} from '@ionic/vue';

import {person, add, pencil} from "ionicons/icons"
import AddCongeModal from "../components/AddCongeModal.vue"
import DetailsPhoto from "../components/DetailsPhoto.vue"
import ModifierEmploye from "../components/ModifierEmploye.vue"
export default{
  data(){
    return {
      person,
      add,
      pencil,
       listeEmployes:[
          {
              id:1,
              nom:"Artcal'O",
              prenom:"Lone Wolf",
              age:45,
              genre:"F",
              conge_debut:null,
              conge_fin:null
          },
          {
              id:2,
              nom:"TLW",
              prenom:"Wolverine",
              age:45,
              genre:"F",
              conge_debut:null,
              conge_fin:null
          },
      ]
    }
  },
  components:{
    IonContent,IonHeader,IonIcon,IonButton,
    IonPage, IonTitle, IonToolbar,
    IonList,IonItem,IonLabel
  },
  methods:{
    async ajouterConge(employeId) {
        const modal = await modalController.create({
          component: AddCongeModal,
          componentProps:{idEmployeProps:employeId}
        });
        modal.present();

        const { data, role } = await modal.onWillDismiss();

        if (role === 'confirm') {
          this.message = `Hello, ${data}!`;
        }
        if (role === 'addCongeEmited') {
          let idx = this.listeEmployes.findIndex(x => x.id=data.idEmploye)
          this.listeEmployes[idx].conge_debut=data.conge_debut
          this.listeEmployes[idx].conge_fin=data.conge_fin
          console.log(this.listeEmployes)
        }
    },
    async modifierEmploye() {
        const modal = await modalController.create({
          component: ModifierEmploye,
          componentProps:{employe:{nom:"ArtcalO", prenom:"TLW", age:20}}
        });
        modal.present();

        const { data, role } = await modal.onWillDismiss();

        if (role === 'confirm') {
          this.message = `Hello, ${data}!`;
        }
    },
    async openPhoto() {
        const modal = await modalController.create({
          component: DetailsPhoto,
          componentProps:{photo:"/assets/logo.jpg"},
          backdropDismiss:false,
          animated:true,
        });
        modal.present();

        const { data, role } = await modal.onWillDismiss();

        if (role === 'confirm') {
          this.message = `Hello, ${data}!`;
        }
    },
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
