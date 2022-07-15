<template>
  <div id="roadmap" class="w-full flex justify-center bg-dark mt-20">
    <div
      class="flex md:flex flex-col gap-8 md:gap-14 md:w-[min(120vmin,100%)] pt-6 md:pt-20 px-6 md:px-10 pb-6 md:pb-10"
    >
      <!-- <span class="text-4xl text-white text-left">Roadmap</span> -->
      <div
        class="grid w-full"
        style="grid-template-columns: max-content 1fr; grid-template-rows: 1fr"
      >
        <div
          class="row-start-1 col-start-1 row-end-1 col-end-1 flex flex-col justify-evenly items-start gap-2 md:gap-5"
        >
          <RoadmapLeft
            :open="() => change(0)"
            :opened="open === 0"
            :q="'Q3 2022'"
          />

          <RoadmapLeft
            :open="() => change(1)"
            :opened="open === 1"
            :q="'Q4 2022'"
          />
          <RoadmapLeft
            :open="() => change(2)"
            :opened="open === 2"
            :q="'Q1 2023'"
          />
        </div>
        <div class="row-start-1 col-start-2 row-end-1 col-end-2 grid max-w-3/4">
          <RoadmapRight
            :text="'Launch a simple alpha version consisting of a single protocol that enables users to create private campaigns for their NFT projects.'"
            :opened="open === 0"
            a="flex-start"
            :n="'Alpha'"
          />
          <RoadmapRight
            :text="'Build more features into the product by adding several different protocols thath can be used to created varying experiences for end users.'"
            :opened="open === 1"
            a="center"
            :n="'Launch'"
          />
          <RoadmapRight
            :text="`With a large set of possibilites for people to create using
              Chisel, we'll focus on working with partners on integrating their
              projects with our platform.`"
            :opened="open === 2"
            a="flex-end"
            :n="'Integrations'"
          />
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import RoadmapLeft from "./RoadmapLeft.vue";
import RoadmapRight from "./RoadmapRight.vue";
export default {
  name: "RoadmapThree",
  components: { RoadmapLeft, RoadmapRight },
  data() {
    return { open: 0 };
  },
  methods: {
    change(to) {
      console.log(this.open, to);
      this.open = to;
    },
  },
};
</script>
<style>
@keyframes gutter {
  0% {
    width: 0px;
  }
  100% {
    width: 5rem;
  }
}
@keyframes show {
  0% {
    height: 100%;
  }
  100% {
    height: 0%;
  }
}
</style>
