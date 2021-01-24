<template>
    <ion-page>
        <ion-toolbar color="success">
            <ion-title>Detail Kelas</ion-title>
        </ion-toolbar>

        <ion-content>
            <ion-list>
                <ion-item v-for="(item,id) in kelasdetail" :key="id">
                    <ion-label>Pertemuan {{ item.pertemuan }} </ion-label>
                    <ion-badge color="success" slot="end"> {{ item.status }} </ion-badge>
                </ion-item>
            </ion-list>
        </ion-content>
    </ion-page>
</template>

<script>
    import {
        IonPage,
        IonToolbar,
        IonTitle,
        IonContent,
        IonList,
        IonItem,
        IonLabel,
        IonBadge
    } from '@ionic/vue'
    import { defineComponent } from 'vue'
    import axios from 'axios';

    export default  defineComponent({
        data(){
            return {
                kelasdetail: []
            }
        },
      components: {
          IonPage,
          IonToolbar,
          IonTitle,
          IonContent,
          IonList,
          IonItem,
          IonLabel,
          IonBadge
      },
      mounted(){
          axios.post("http://35.153.33.120/api/kelasdetail",{
              "user_id": localStorage.getItem("user_id"),
              "kelas_id": this.$route.params.id
          })
          .then(response => {
              this.kelasdetail = response.data.data
          })
      }  
    })
</script>

<style scoped>

</style>