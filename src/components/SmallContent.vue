<template>
  <div
    id="header"
    class="w-full md:hidden lg:hidden lg:w-[140vmin] px-6 pt-6 md:px-8 md:pt-8 lg:pt-10 lg:px-10"
  >
    <div class="flex justify-between items-center md:hidden lg:hidden">
      <div class="flex items-center gap-4 clickable">
        <img :src="logo" alt="logo" class="h-8 w-8" />
        <div class="flex self-stretch items-center">
          <span class="text-[24px] leading-none text-white">Chisel</span>
        </div>
      </div>
      <div class="grid">
        <MenuIconVue
          :onclick="() => (opened = !opened)"
          :style="
            'grid-column: 1; grid-row: 1; transition: 0.15s all linear;' +
            (opened ? 'z-index: 1;' : 'z-index: 2;') +
            (opened ? 'opacity: 0;' : 'opacity: 1;')
          "
          class="h-4 w-4 cursor-pointer"
          alt="menu"
        />
        <CloseIconVue
          alt="close"
          class="h-4 w-4 cursor-pointer"
          :onclick="() => (opened = !opened)"
          :style="
            'grid-column: 1; grid-row: 1; transition: 0.15s all linear;' +
            (opened ? 'z-index: 2;' : 'z-index: 1;') +
            (opened ? 'opacity: 1;' : 'opacity: 0;')
          "
        />
      </div>
    </div>
  </div>
  <div
    class="mt-6 overflow-hidden w-full h-0 md:hidden lg:hidden"
    :style="'transition: 0.3s all linear;' + (opened ? 'height: 240px;' : '')"
  >
    <div
      class="flex flex-col items-end gap-6"
      :style="
        'transition: 0.3s all linear;' +
        (opened
          ? 'transform: translateY(0px);'
          : 'transform: translateY(-240px);')
      "
    >
      <div class="h-6 flex items-center justify-end">
        <span class="hover:text-primary clickable">App</span>
      </div>
      <div class="h-6 flex items-center justify-end">
        <span class="hover:text-primary clickable">Docs</span>
      </div>
      <div class="h-6 flex items-center justify-end">
        <span class="hover:text-primary clickable">Blog</span>
      </div>
      <div class="h-6 flex items-center justify-end">
        <span class="hover:text-primary clickable">Jobs</span>
      </div>
      <div class="h-6 flex items-center justify-end gap-6">
        <TwitterIcon alt="Twitter" class="h-6 w-6 clickable" />
        <GithubIcon alt="Github" class="h-6 w-6 clickable" />
        <DiscordIcon alt="Discord" class="h-6 w-6 clickable" />
      </div>
      <div></div>
    </div>
  </div>
  <div id="main" class="md:hidden lg:hidden grow w-full bg-dark">
    <div
      class="px-6 pt-6 mt-10 gap-8 w-full flex flex-col items-center text-center md:hidden lg:hidden"
    >
      <span class="text-4xl px-4 text-white"
        >A Tool for Digital Collectibles</span
      >
      <span class="text-xl px-4"
        >Chisel is the missing piece to unleash the true power of NFT's</span
      >
      <div class="flex items-center gap-6 flex-wrap justify-center">
        <div
          class="clickable font-medium bg-secondary text-white border-solid border-2 border-secondary py-2 px-3.5"
        >
          Launch App
        </div>
        <div
          class="clickable font-medium text-primary border-solid border-2 border-primary py-2 px-3.5"
        >
          Join Discord
        </div>
      </div>
    </div>
    <div
      class="md:hidden lg:hidden mt-20 px-8 pt-6 flex flex-col items-center gap-8"
    >
      <span class="text-xl">Built with</span>
      <div class="flex justify-evenly items-center flex-wrap gap-7">
        <ChainlinkIcon class="w-28 max-h-12" />
        <FilecoinIcon class="w-28 max-h-14" />
        <UniswapIcon class="w-28 max-h-12" />
      </div>
    </div>
    <div
      class="px-6 pt-6 mt-20 md:hidden lg:hidden flex flex-col items-center gap-16"
    >
      <div class="flex flex-col items-center gap-5">
        <ShushIcon class="h-20 w-20 text-secondary" />
        <span class="text-2xl text-white font-bold">Privacy</span>
        <span class="text-center text-lg max-w-[min(75%,350px)]"
          >Mint and trade pictures on the Blockchain without ever having to
          wonder who leaked your content</span
        >
      </div>
      <div class="flex flex-col items-center gap-5">
        <ContractIcon class="h-24 w-24 text-secondary" />
        <span class="text-2xl text-white font-bold">Authenticity</span>
        <span class="text-center text-lg max-w-[min(75%,350px)]"
          >Buyers can be confident in the legitimacy of a seller's NFT with the
          use of encryption and Smart Contracts</span
        >
      </div>
      <div class="flex flex-col items-center gap-5">
        <BlocksIcon class="h-20 w-20 text-secondary" />
        <span class="text-2xl text-white font-bold">Trustless</span>
        <span class="text-center text-lg max-w-[min(75%,350px)]"
          >Chisel takes away the middle-man by being a simple tool anyone can
          use without having to rely on a third party</span
        >
      </div>
    </div>
    <div
      class="flex flex-col items-center gap-6 md:hidden lg:hidden mt-20 mb-20 px-6 pt-6"
    >
      <span class="text-white text-2xl"
        >Craft unique experiences for your fans</span
      >
      <span class="text-lg 5 text-center"
        >Use chisel to add novel and useful components to your project. Attract
        users by offering something that stands out in the market.
      </span>
      <form class="flex items-center">
        <input
          type="email"
          class="outline-none text-dark w-2/3 min-w-[120px] self-stretch items-stretch px-4 border-solid border-2 border-light focus:border-primary"
          placeholder="Your Email"
        />
        <input
          class="flex min-w-[max(33.333333,120px) font-medium text-white clickable items-center justify-center px-6 py-3 leading-none bg-primary"
          type="submit"
          value="Stay Posted"
        />
      </form>
    </div>
  </div>
  <div
    id="footer"
    class="md:hidden lg:hidden bg-dark w-full flex flex-col gap-4 px-6 pt-6 pb-6"
  >
    <div class="flex flex-col gap-3">
      <span class="text-white font-bold">Company</span>
      <div class="flex items-stretch flex-wrap">
        <span class="mr-6 mb-3">App</span>
        <span class="mr-6 mb-3">Docs</span>
        <span class="mr-6 mb-3">Blog</span>
        <span class="mb-3">Jobs</span>
      </div>
    </div>
    <div class="flex flex-col gap-3">
      <span class="text-white font-bold">Socials</span>
      <div class="flex items-center flex-wrap">
        <span class="mr-6 mb-3">Twitter</span>
        <span class="mr-6 mb-3">Discord</span>
        <span class="mr-6 mb-3">Github</span>
        <span class="mb-3">Email</span>
      </div>
    </div>
    <div class="flex justify-between items-center">
      <span>Copyright Chisel</span>
      <span>Made with 💖</span>
    </div>
  </div>
</template>
<script>
export default {
  name: "SmallContent",
};
</script>
