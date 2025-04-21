<script setup lang="ts">
import ImageCarousel from "./components/CustomCarousel.vue";
import sampleImage from "./assets/images/check.jpg";
import sampleImage2 from "./assets/images/new.jpg";

const carouselImages = [
  {
    image: sampleImage2,
    title: "Tranquil Forest",
    subtitle: "A peaceful escape into nature",
  },
  {
    image: sampleImage2,
    title: "Mountain Majesty",
    subtitle: "Breathtaking views from above the clouds",
  },
  {
    image: sampleImage2,
    title: "Urban Vibes",
    subtitle: "Life in the fast lane of the city",
  },
  {
    image: sampleImage2,
    title: "Sunset Bliss",
    subtitle: "Golden hour over the horizon",
  },
  {
    image: sampleImage,
    title: "Ocean Calm",
    subtitle: "Gentle waves and salty air",
  },
  {
    image: sampleImage2,
    title: "Snowy Escape",
    subtitle: "Chilly winds and snowy peaks",
  },
  {
    image: sampleImage,
    title: "Desert Trails",
    subtitle: "The beauty of endless dunes",
  },
  {
    image: sampleImage2,
    title: "Countryside Charm",
    subtitle: "Where time slows down",
  },
  {
    image: sampleImage,
    title: "Night Lights",
    subtitle: "The city that never sleeps",
  },
  {
    image: sampleImage2,
    title: "Coastal Roadtrip",
    subtitle: "Drive by the sea with the breeze",
  },
];
</script>

<template>
  <ImageCarousel
    :images="carouselImages"
    title="Explore Beautiful Places"
    subtitle=""
    :numVisible="4"
    :numScroll="1"
    :circular="false"
    :showSideNavigation="true"
    :showBottomNavigation="true"
    customClass="cursor-pointer rounded-full p-1"
    sideArrowBgColor="bg-orange-600"
    sideArrowTextColor="text-white"
  />
</template>
