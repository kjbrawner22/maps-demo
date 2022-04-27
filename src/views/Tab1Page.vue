<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Tab 1</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Geolocation Demo</ion-title>
        </ion-toolbar>
      </ion-header>
      <ion-button v-on:click="printCurrentPosition" >Get Current Position</ion-button>
      <ion-item>
        <ion-label>Latitude: {{ coordinates.coords.latitude }}</ion-label>
      </ion-item>
      <ion-item>
        <ion-label>Longitude: {{ coordinates.coords.longitude }}</ion-label>
      </ion-item>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { IonButton, IonPage, IonHeader, IonToolbar, IonTitle, IonContent, IonItem, IonLabel } from '@ionic/vue';
import { Geolocation } from '@capacitor/geolocation';

export default  defineComponent({
  name: 'Tab1Page',
  components: { IonButton, IonHeader, IonToolbar, IonTitle, IonContent, IonPage, IonItem, IonLabel },
  data() {
    return {
      coordinates: {
        coords: {
          latitude: 0,
          longitude: 0
        }
      }
    }
  },
  methods: {
    async printCurrentPosition(event: any) {
      const coordinates = await Geolocation.getCurrentPosition();

      this.coordinates = coordinates
    }
  }
});
</script>
