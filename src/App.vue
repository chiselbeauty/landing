<template>
  <div
    v-show="submitted"
    class="overflow-hidden bg-dark text-light w-full h-full absolute flex flex-col items-center justify-center"
  >
    <div
      class="w-full flex justify-center flex-col items-center h-full w-full lg:w-[min(120vmin,100%)] px-6 pt-6 md:px-8 md:pt-8 lg:pt-10 lg:px-10 pb-6 md:pb-8 lg:pb-10"
    >
      <div class="grow"></div>
      <span class="text-8xl mb-10">🎉</span>
      <span class="text-xl text-center mb-4"
        >Your request was successfully processed.</span
      >
      <span class="text-4xl text-center mb-10"
        >Thanks for showing some love!</span
      >
      <span
        :onclick="() => (submitted = false)"
        class="clickable cursor-pointer select-none py-2 px-3.5 border-complement border-2 border-solid text-complement font-medium"
        >Go back</span
      >
      <div class="grow flex items-end justify-center">
        <div
          class="flex items-center gap-4 clickable"
          :onclick="() => (submitted = false)"
        >
          <img :src="logo" alt="logo" class="h-8 w-8" />
          <div class="flex self-stretch items-center">
            <span class="text-[24px] leading-none text-white">Chisel</span>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div
    id="App"
    v-show="!submitted"
    class="overflow-hidden text-light w-full min-h-full absolute flex flex-col items-center justify-between"
  >
    <div class="w-full bg-dark flex justify-center">
      <div
        id="header"
        class="w-full lg:w-[min(120vmin,100%)] px-6 pt-6 md:px-8 md:pt-8 lg:pt-10 lg:px-10"
      >
        <div class="flex justify-between items-center lg:hidden">
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
        <div
          class="mt-6 overflow-hidden w-full h-0 lg:hidden"
          :style="
            'transition: 0.3s all linear;' + (opened ? 'height: 240px;' : '')
          "
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
              <span
                :onclick="() => navigate('https://app.chisel.beauty')"
                class="hover:text-primary clickable"
                >App</span
              >
            </div>
            <!-- <div class="h-6 flex items-center justify-end">
              <span
                :onclick="() => navigate('https://docs.chisel.beauty')"
                class="hover:text-primary clickable"
                >Docs</span
              >
            </div> -->
            <div class="h-6 flex items-center justify-end">
              <span
                :onclick="() => navigate('https://blog.chisel.beauty')"
                class="hover:text-primary clickable"
                >Blog</span
              >
            </div>
            <div class="h-6 flex items-center justify-end">
              <span
                :onclick="
                  () => navigate('https://angel.co/company/chisel-protocol-1')
                "
                class="hover:text-primary clickable"
                >Jobs</span
              >
            </div>
            <div class="h-6 flex items-center justify-end gap-6">
              <TwitterIcon
                :onclick="() => navigate('https://twitter.com/chiselbeauty')"
                alt="Twitter"
                class="h-6 w-6 clickable"
              />
              <GithubIcon
                :onclick="() => navigate('https://github.com/chiselbeauty')"
                alt="Github"
                class="h-6 w-6 clickable"
              />
              <DiscordIcon
                :onclick="() => navigate('https://discord.gg/hmGCCJkgun')"
                alt="Discord"
                class="h-6 w-6 clickable"
              />
            </div>
            <div></div>
          </div>
        </div>
        <!-- <div
          class="w-full flex pb-8 justify-between items-center hidden md:flex lg:hidden"
        >
          <div class="flex gap-8 items-center">
            <img :src="logo" alt="logo" class="h-8 w-8 clickable" />
            <div class="flex gap-8 items-center">
              <div class="self-stretch flex items-center">
                <span class="hover:text-primary clickable text-lg">App</span>
              </div>
              <div class="self-stretch flex items-center">
                <span class="hover:text-primary clickable text-lg">Docs</span>
              </div>
              <div class="self-stretch flex items-center">
                <span class="hover:text-primary clickable text-lg">Blog</span>
              </div>
              <div class="self-stretch flex items-center">
                <span class="hover:text-primary clickable text-lg">Jobs</span>
              </div>
            </div>
          </div>
          <div class="flex gap-8 items-center justify-end">
            <TwitterIcon alt="Twitter" class="clickable h-5 w-5" />
            <GithubIcon alt="Github" class="clickable h-5 w-5" />
            <DiscordIcon alt="Discord" class="clickable h-5 w-5" />
          </div>
        </div> -->
        <div class="hidden lg:flex justify-between items-center w-full pb-10">
          <div class="flex gap-10 items-center">
            <div class="clickable flex gap-5 items-center">
              <img :src="logo" alt="logo" class="h-10 w-10" />
              <div class="flex self-stretch items-center">
                <span class="text-white leading-none text-[36px]">Chisel</span>
              </div>
            </div>
            <div class="flex gap-10 items-center">
              <div class="self-stretch flex items-center">
                <span
                  :onclick="() => navigate('https://app.chisel.beauty')"
                  class="hover:text-primary clickable text-xl"
                  >App</span
                >
              </div>
              <!-- <div class="self-stretch flex items-center">
                <span
                  :onclick="() => navigate('https://docs.chisel.beauty')"
                  class="hover:text-primary clickable text-xl"
                  >Docs</span
                >
              </div> -->
              <div class="self-stretch flex items-center">
                <span
                  :onclick="() => navigate('https://blog.chisel.beauty')"
                  class="hover:text-primary clickable text-xl"
                  >Blog</span
                >
              </div>
              <div class="self-stretch flex items-center">
                <span
                  :onclick="
                    () => navigate('https://angel.co/company/chisel-protocol-1')
                  "
                  class="hover:text-primary clickable text-xl"
                  >Jobs</span
                >
              </div>
            </div>
          </div>
          <div class="flex justify-end items-center gap-10">
            <TwitterIcon
              :onclick="() => navigate('https://twitter.com/chiselbeauty')"
              alt="Twitter"
              class="clickable h-6 w-6"
            />
            <GithubIcon
              :onclick="() => navigate('https://github.com/chiselbeauty')"
              alt="Github"
              class="clickable h-6 w-6"
            />
            <DiscordIcon
              :onclick="() => navigate('https://discord.gg/hmGCCJkgun')"
              alt="Discord"
              class="clickable h-6 w-6"
            />
          </div>
        </div>
      </div>
    </div>
    <div id="main" class="grow w-full bg-dark">
      <div
        class="px-6 pt-6 mt-10 gap-8 w-full flex flex-col items-center text-center lg:w-[min(120vmin, 100%)]"
      >
        <span class="text-4xl px-4 text-white"
          >A Tool for Digital Collectibles</span
        >
        <span class="text-xl px-4"
          >Chisel provides the missing pieces to help users unlock the full
          potential of NFT's</span
        >
        <div class="flex items-center gap-6 flex-wrap justify-center">
          <div
            class="clickable font-medium bg-secondary text-white border-solid border-2 border-secondary py-2 px-3.5"
            :onclick="() => navigate('https://app.chisel.beauty')"
          >
            Launch App
          </div>
          <div
            class="clickable font-medium text-primary border-solid border-2 border-primary py-2 px-3.5"
            :onclick="() => navigate('https://discord.gg/hmGCCJkgun')"
          >
            Join Discord
          </div>
        </div>
      </div>
      <div
        class="lg:w-[min(120vmin, 100%)] mt-20 px-8 pt-6 flex flex-col items-center gap-8"
      >
        <span class="text-xl">Built with</span>
        <div class="flex justify-evenly items-center flex-wrap gap-7">
          <ChainlinkIcon class="w-28 max-h-12" />
          <FilecoinIcon class="w-28 max-h-14" />
          <UniswapIcon class="w-28 max-h-12" />
        </div>
      </div>
      <div class="w-full flex justify-center">
        <div
          class="px-6 pt-6 mt-20 lg:w-[min(120vmin,100%)] flex flex-col lg:flex-row items-center gap-16 lg:pt-10 lg:px-10"
        >
          <div class="flex flex-col items-center gap-5">
            <ShushIcon class="h-20 w-20 text-secondary" />
            <span class="text-2xl text-white font-bold">Private</span>
            <span
              class="text-center text-lg max-w-[min(75%,350px)] lg:max-w-full"
              >Mint and trade pictures on the Blockchain without ever having to
              wonder who leaked your content</span
            >
          </div>
          <div class="flex flex-col items-center gap-5">
            <ContractIcon class="h-24 w-24 text-secondary" />
            <span class="text-2xl text-white font-bold">Verifiable</span>
            <span
              class="text-center text-lg max-w-[min(75%,350px)] lg:max-w-full"
              >Buyers can be confident in the legitimacy of a seller's NFT with
              the use of encryption and Smart Contracts</span
            >
          </div>
          <div class="flex flex-col items-center gap-5">
            <BlocksIcon class="h-20 w-20 text-secondary" />
            <span class="text-2xl text-white font-bold">Trustless</span>
            <span
              class="text-center text-lg max-w-[min(75%,350px)] lg:max-w-full"
              >Chisel takes away the middle-man by being a simple tool anyone
              can use without having to rely on a third party</span
            >
          </div>
        </div>
      </div>
      <Roadmap />
      <div class="flex flex-col items-center gap-6 mt-20 mb-20 px-6 pt-6">
        <span class="text-white text-center text-2xl"
          >Craft unique experiences for your fans</span
        >
        <span class="text-lg 5 text-center md:text-center md:w-3/4 lg:w-1/2"
          >Use chisel to add novel and useful components to your project.
          Attract users by offering something that stands out in the market.
        </span>
        <iframe
          class=""
          id="res"
          name="res"
          style="width: 0; height: 0"
        ></iframe>
        <div style="display: grid">
          <form
            class="flex items-center"
            action="https://beauty.us14.list-manage.com/subscribe/post?u=eaa7024d4ff006534c1e5b6ee&amp;id=e4cc35834e"
            method="post"
            id="mc-embedded-subscribe-form"
            name="mc-embedded-subscribe-form"
            style="grid-column: 1; grid-row: 1"
            target="res"
          >
            <input
              name="EMAIL"
              id="mce-EMAIL"
              type="email"
              class="outline-none text-dark w-2/3 min-w-[120px] self-stretch items-stretch px-4 border-solid border-2 border-light focus:border-primary"
              placeholder="Your Email"
              :value="email"
            />
            <input
              type="text"
              name="b_eaa7024d4ff006534c1e5b6ee_e4cc35834e"
              tabindex="-1"
              value=""
              style="display: none"
            />
            <div class="grid bg-primary text-white font-medium clickable">
              <input
                class="flex min-w-[max(33.333333,120px) font-medium text-white clickable items-center justify-center px-6 py-3 leading-none bg-primary"
                type="submit"
                value="Subscribe"
                name="subscribe"
                id="mc-embedded-subscribe"
                style="opacity: 0; grid-column: 1; grid-row: 1"
              />
              <div
                class="flex items-center justify-center"
                style="grid-column: 1; grid-row: 1"
              >
                Stay Posted
              </div>
            </div>
          </form>
          <form
            class="flex items-center"
            style="grid-column: 1; grid-row: 1"
            :onsubmit="submit"
          >
            <input
              type="email"
              class="outline-none text-dark w-2/3 min-w-[120px] self-stretch items-stretch px-4 border-solid border-2 border-light focus:border-primary"
              placeholder="Your Email"
              v-model="email"
              required
            />
            <input
              type="text"
              name="b_eaa7024d4ff006534c1e5b6ee_e4cc35834e"
              tabindex="-1"
              value=""
              style="display: none"
            />
            <div class="grid bg-primary text-white font-medium clickable">
              <input
                class="flex min-w-[max(33.333333,120px) font-medium text-white clickable items-center justify-center px-6 py-3 leading-none bg-primary"
                type="submit"
                value="Subscribe"
                style="opacity: 0; grid-column: 1; grid-row: 1"
                :disabled="submitting"
              />
              <div
                class="flex items-center justify-center"
                style="grid-column: 1; grid-row: 1"
              >
                <span v-if="!submitting">Stay Posted</span>
                <div
                  v-else
                  style="
                    border-radius: 50%;
                    border-top: 4px solid white;
                    height: 24px;
                    width: 24px;
                    animation: spin 2s linear infinite;
                  "
                ></div>
              </div>
            </div>
          </form>
        </div>
      </div>
    </div>
    <div
      class="flex justify-center w-full bg-dark border-t-light border-t-solid border-t-2"
    >
      <div
        id="footer"
        class="w-full flex flex-col gap-4 px-6 pt-6 pb-6 lg:pt-10 lg:px-10 lg:w-[min(120vmin,100%)]"
      >
        <div class="flex flex-col gap-3">
          <span class="text-white font-bold">Company</span>
          <div class="flex items-stretch flex-wrap">
            <span
              :onclick="() => navigate('https://app.chisel.beauty')"
              class="mr-6 mb-3 hover:text-primary clickable"
              >App</span
            >
            <!-- <span
              :onclick="() => navigate('https://docs.chisel.beauty')"
              class="mr-6 mb-3 hover:text-primary clickable"
              >Docs</span
            > -->
            <span
              :onclick="() => navigate('https://blog.chisel.beauty')"
              class="mr-6 mb-3 hover:text-primary clickable"
              >Blog</span
            >
            <span
              :onclick="
                () => navigate('https://angel.co/company/chisel-protocol-1')
              "
              class="mb-3 hover:text-primary clickable"
              >Jobs</span
            >
          </div>
        </div>
        <div class="flex flex-col gap-3">
          <span class="text-white font-bold">Socials</span>
          <div class="flex items-center flex-wrap">
            <span
              :onclick="() => navigate('https://twitter.com/chiselbeauty')"
              class="mr-6 mb-3 hover:text-primary clickable"
              >Twitter</span
            >
            <span
              :onclick="() => navigate('https://github.com/chiselbeauty')"
              class="mr-6 mb-3 hover:text-primary clickable"
              >Github</span
            >
            <span
              :onclick="() => navigate('https://discord.gg/hmGCCJkgun')"
              class="mr-6 mb-3 hover:text-primary clickable"
              >Discord</span
            >
            <span
              :onclick="() => navigate('mailto:contact@chisel.beauty')"
              class="mb-3 hover:text-primary clickable"
              >Email</span
            >
          </div>
        </div>
        <div class="flex justify-between items-center">
          <span>© Chisel Protocol</span>
          <span>Made with 💖</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import logo from "./assets/chisel.png";
import TwitterIcon from "./components/icons/TwitterIcon.vue";
import GithubIcon from "./components/icons/GithubIcon.vue";
import DiscordIcon from "./components/icons/DiscordIcon.vue";
import MenuIconVue from "./components/icons/MenuIcon.vue";
import CloseIconVue from "./components/icons/CloseIcon.vue";
import BlocksIcon from "./components/icons/BlocksIcon.vue";
import ShushIcon from "./components/icons/ShushIcon.vue";
import ContractIcon from "./components/icons/ContractIcon.vue";
import ChainlinkIcon from "./components/icons/ChainlinkIcon.vue";
import FilecoinIcon from "./components/icons/FilecoinIcon.vue";
import UniswapIcon from "./components/icons/UniswapIcon.vue";
import Roadmap from "./components/Roadmap3.vue";
export default {
  name: "App",
  components: {
    Roadmap,
    TwitterIcon,
    GithubIcon,
    DiscordIcon,
    MenuIconVue,
    CloseIconVue,
    BlocksIcon,
    ShushIcon,
    ContractIcon,
    ChainlinkIcon,
    FilecoinIcon,
    UniswapIcon,
  },
  data() {
    return {
      opened: false,
      logo,
      email: "",
      submitted: false,
      submitting: false,
    };
  },

  methods: {
    navigate(href) {
      window.location.href = href;
    },
    submit(e) {
      e.preventDefault();
      this.submitting = true;
      document.getElementById("mc-embedded-subscribe-form").submit();
      const checkAndReport = () => {
        if (document.getElementById("res").contentWindow.document.body) {
          this.submitted = true;
          this.submitting = false;
          setTimeout(() => {
            document.getElementById("res").src = "";
          }, 1000);
          this.email = "";
        } else {
          setTimeout(() => checkAndReport(), 100);
        }
      };
      checkAndReport();
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}
body {
  margin: 0;
}
.clickable {
  user-select: none;
  cursor: pointer;
  transition: 0.1s all linear;
  opacity: 1;
  transform: translate3d(0, 0, 0);
}

.clickable:active {
  opacity: 0.8;
  transform: translate3d(1px, 1px, 0px);
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>
