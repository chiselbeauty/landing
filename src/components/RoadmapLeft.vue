<template>
  <div class="flex items-stretch">
    <div
      class="flex md:hidden items-center justify-start pr-6 lg:pr-20 flex-wrap gap-2"
    >
      <span :class="`text-white text-lg md:text-2xl `">{{ q }}</span>
    </div>
    <div
      class="hidden md:flex flex-col items-start justify-center pr-6 md:pr-10"
    >
      <span class="text-white text-lg md:text-2xl">{{ q }}</span>
    </div>
    <div class="flex items-center justify-center pr-6 md:pr-10">
      <div
        @click="open"
        :class="
          'clickable leading-none rounded-full border-light border-2 border-solid w-3 h-3 md:w-4 md:h-4' +
          (opened ? ' bg-light' : ' bg-dark')
        "
      ></div>
    </div>
    <div
      class="hidden md:flex flex-col justify-stretch items-start w-6 md:w-20"
    >
      <div
        :class="`grow border-b-[1px] border-solid border-light w-0 ${
          opened ? 'sm:gutter md:big-gutter' : ''
        }`"
        :style="opened ? 'animation: gutter 0.15s linear forwards' : ''"
      ></div>
      <div
        class="grow border-t-[1px] border-solid border-light w-0"
        :style="opened ? 'animation: gutter 0.15s linear forwards' : ''"
      ></div>
    </div>
  </div>
</template>
<script>
export default {
  name: "RoadmapLeft",
  props: ["opened", "open", "q", "n"],
};
</script>
<style>
.big-gutter {
  animation: bigGutter 0.15s linear forwards;
}
.gutter {
  animation: gutter 0.15s linear forwards;
}
@keyframes gutter {
  0% {
    width: 0px;
  }
  100% {
    width: 2.25rem;
  }
}
@keyframes bigGutter {
  0% {
    width: 0px;
  }
  100% {
    width: 5rem;
  }
}
</style>
