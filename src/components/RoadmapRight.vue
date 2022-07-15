<template>
  <div
    class="grid row-start-1 row-end-1 col-start-1 col-end-1 pt-1"
    :style="opened ? 'z-index: 3' : 'z-index: 1'"
  >
    <!-- <div
              class="row-start-1 row-end-1 col-start-1 col-end-1 flex items-stretch justify-stretch"
            ></div> -->
    <div
      class="w-full row-start-1 row-end-2 col-start-1 col-end-1 flex items-center"
      :style="`align-items: ${a}`"
    >
      <div
        class="flex flex-col justify-start items-start gap-2 md:gap-5 text-left w-full border-l-2 border-solid border-light pl-6 md:pl-10 md:py-5 md:pr-10"
      >
        <span
          :class="
            `leading-none text-lg md:text-3xl text-white text-bold ` +
            (opened
              ? 'border-b-2 border-solid border-complement'
              : 'border-b-2')
          "
          >{{ n }}</span
        >
        <span class="text-lg md:text-3xl">{{ text }}</span>
      </div>
    </div>
    <div
      style="z-index: 2"
      class="row-start-1 row-end-1 col-start-1 col-end-1 flex flex-col items-stretch justify-center"
    >
      <div class="flex items-start h-1/2">
        <div
          class="h-full w-full bg-dark border-l-2 border-solid border-dark"
          :style="
            opened ? 'animation: show 0.3s ease-in-out 0.15s forwards' : ''
          "
        ></div>
      </div>
      <div class="flex items-end h-1/2">
        <div
          class="h-full w-full bg-dark border-l-2 border-solid border-dark"
          :style="
            opened ? 'animation: show 0.3s ease-in-out 0.15s forwards' : ''
          "
        ></div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "RoadmapRight",
  props: ["text", "opened", "a", "n"],
};
</script>
<style>
@keyframes show {
  0% {
    height: 100%;
  }
  100% {
    height: 0%;
  }
}
</style>
