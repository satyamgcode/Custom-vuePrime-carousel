<template>
  <div class="p-6 bg-[#E5F6F3] min-h-screen rounded-3xl relative">
    <h2 class="text-xl font-semibold mb-6 text-center">{{ title }}</h2>

    <div class="relative max-w-[80vw] mx-auto">
      <!-- Side Arrows -->
      <p
        v-if="showSideNavigation"
        @click="prev"
        :class="[
          'absolute top-[45%] left-[-1.5rem] -translate-y-1/2 z-10',
          customClass,
          sideArrowBgColor,
          sideArrowTextColor,
        ]"
      >
        <i class="pi pi-angle-left text-2xl"></i>
      </p>

      <p
        v-if="showSideNavigation"
        @click="next"
        :class="[
          'absolute top-[45%] right-[-1.5rem] -translate-y-1/2 z-10',
          customClass,
          sideArrowBgColor,
          sideArrowTextColor,
        ]"
      >
        <i class="pi pi-angle-right text-2xl"></i>
      </p>

      <Carousel
        :value="images"
        :responsiveOptions="computedResponsiveOptions"
        :numVisible="numVisible"
        :numScroll="numScroll"
        :circular="circular"
        :showIndicators="true"
        :showNavigators="false"
        ref="carouselRef"
        class="max-w-[80vw] mx-auto"
      >
        <template #item="{ data, index }">
          <div class="p-3 h-full">
            <div
              class="border rounded-xl shadow-md overflow-hidden bg-white h-full flex flex-col"
            >
              <img
                :src="data.image"
                :alt="`Image ${index + 1}`"
                class="w-full h-[200px] object-cover"
              />
              <div class="p-4 flex-1 flex flex-col justify-between">
                <h3 class="font-bold mb-2">{{ data.title }}</h3>
                <p class="text-gray-700">
                  {{ data.subtitle || defaultSubtitle }}
                </p>
              </div>
            </div>
          </div>
        </template>
      </Carousel>

      <!-- Bottom Navigation -->
      <div
        v-if="showBottomNavigation"
        class="flex justify-center items-center gap-6 mt-6"
      >
        <p
          @click="prev"
          :class="[
            'transition',
            customClass,
            sideArrowBgColor,
            sideArrowTextColor,
          ]"
        >
          <i class="pi pi-angle-left text-xl"></i>
        </p>
        <p
          @click="next"
          :class="[
            'transition',
            customClass,
            sideArrowBgColor,
            sideArrowTextColor,
          ]"
        >
          <i class="pi pi-angle-right text-xl"></i>
        </p>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from "vue";
import Carousel from "primevue/carousel";
import "primeicons/primeicons.css";

interface CarouselImage {
  image: string;
  title: string;
  subtitle?: string;
}

const props = defineProps<{
  images: CarouselImage[];
  title?: string;
  subtitle?: string;
  numVisible?: number;
  numScroll?: number;
  circular?: boolean;
  sideArrowBgColor?: string;
  sideArrowTextColor?: string;
  showSideNavigation?: boolean;
  showBottomNavigation?: boolean;
  customClass?: string;
}>();

const carouselRef = ref<InstanceType<typeof Carousel> | null>(null);

const numVisible = props.numVisible ?? 3;
const numScroll = props.numScroll ?? 1;
const circular = props.circular ?? false;
const defaultSubtitle = props.subtitle ?? "This component is just for demo";

const sideArrowBgColor = props.sideArrowBgColor || "";
const sideArrowTextColor = props.sideArrowTextColor || "text-orange-500";
const customClass = computed(() => props.customClass || "cursor-pointer");
const showSideNavigation = props.showSideNavigation ?? true;
const showBottomNavigation = props.showBottomNavigation ?? false;

const computedResponsiveOptions = computed(() => [
  { breakpoint: "1400px", numVisible: 3, numScroll: 1 },
  { breakpoint: "1199px", numVisible: 3, numScroll: 1 },
  { breakpoint: "991px", numVisible: 2, numScroll: 1 },
  { breakpoint: "767px", numVisible: 1, numScroll: 1 },
]);

const next = (): void => {
  carouselRef.value?.navForward();
};

const prev = (): void => {
  carouselRef.value?.navBackward();
};
</script>
