<template>
  <ion-page>
    <ion-header>
      <ion-toolbar>
        <ion-title>Weather Forecast</ion-title>
      </ion-toolbar>
    </ion-header>

    <ion-content class="ion-padding">
      <ion-card v-if="weatherData">
        <ion-card-header>
          <ion-card-title>{{ weatherData.realtime.text }}</ion-card-title>
        </ion-card-header>
        <ion-card-content>
          <div class="weather-info">
            <div class="weather-icon">
              <ion-icon :name="getWeatherIconName()"></ion-icon>
            </div>
            <div class="weather-details">
              <div class="temperature">{{ weatherData.realtime.temp }} °C</div>
              <div class="description">
                {{ weatherData.realtime.text }}
              </div>
            </div>
          </div>
        </ion-card-content>
      </ion-card>

      <ion-button expand="block" @click="getCurrentWeather"
        >Get Current Weather</ion-button
      >
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { CapacitorHttp } from '@capacitor/core'

const weatherData = ref(null)

const getCurrentWeather = async () => {
  // const { Geolocation, Http } = Plugins

  // const coordinates = await Geolocation.getCurrentPosition()
  const { latitude, longitude } = { latitude: 116.447962, longitude: 39.958751 }

  const url = `https://eolink.o.apispace.com/456456/weather/v001/now?lonlat=${latitude}%2C${longitude}`
  const response = await CapacitorHttp.get({
    url,
    headers: {
      'X-APISpace-Token': '8wh6gf8rpw2gs128oz1apoyte54a0k9a',
    },
  })

  weatherData.value = response.data.result
  console.log('===', weatherData.value)
}

const getWeatherIconName = () => {
  if (weatherData.value) {
    return `weather-`
  }
  return ''
}
</script>

<style scoped>
.weather-info {
  display: flex;
  align-items: center;
}

.weather-icon {
  font-size: 4rem;
  margin-right: 1rem;
}

.weather-details {
  display: flex;
  flex-direction: column;
}

.temperature {
  font-size: 2rem;
  font-weight: bold;
}

.description {
  margin-top: 0.5rem;
}
</style>
