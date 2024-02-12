<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Tab 3</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Tab 3</ion-title>
        </ion-toolbar>
      </ion-header>
      <van-field
        class="van-input"
        v-model="mobile"
        type="tel"
        placeholder="请输入手机号"
        clearable
        maxlength="11"
      />
      <!-- <ExploreContainer name="Tab 3 page" /> -->
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import {
  IonPage,
  IonHeader,
  IonToolbar,
  IonTitle,
  IonContent,
} from '@ionic/vue'
// import ExploreContainer from '@/components/ExploreContainer.vue'
import { ref } from 'vue'
const mobile = ref('')
</script>
