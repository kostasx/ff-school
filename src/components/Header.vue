<template>
  <nav id="header" class="nav fixed w-full z-30 top-0 text-white">
    <div class="w-full mx-auto flex flex-wrap items-center justify-between">
      <!-- Navigation drawer -->
      <div class="block lg:hidden p-4">
        <button
          aria-label="Open Menu"
          @click="drawer"
          id="nav-toggle"
          class="flex items-center p-1 text-white hover:text-yellow-700"
        >
          <svg
            class="fill-current h-6 w-6"
            viewBox="0 0 20 20"
            xmlns="http://www.w3.org/2000/svg"
          >
            <title>Front-End Foxes School</title>
            <path d="M0 3h20v2H0V3zm0 6h20v2H0V9zm0 6h20v2H0v-2z" />
          </svg>
        </button>
        <!--overlay for open side menu-->
        <transition
          enter-class="opacity-0"
          enter-active-class="ease-out transition-medium"
          enter-to-class="opacity-100"
          leave-class="opacity-100"
          leave-active-class="ease-out transition-medium"
          leave-to-class="opacity-0"
        >
          <div
            @keydown.esc="isOpen = false"
            v-show="isOpen"
            class="z-10 fixed inset-0 transition-opacity"
          >
            <div
              @click="isOpen = false"
              class="absolute inset-0 bg-black opacity-50"
              tabindex="0"
            ></div>
          </div>
        </transition>
        <aside
          id="drawer"
          class="
            transform
            top-0
            left-0
            w-64
            fixed
            h-full
            overflow-auto
            ease-in-out
            transition-all
            duration-300
            z-30
          "
          :class="isOpen ? 'translate-x-0' : '-translate-x-full'"
        >
          <ul>
            <li @click="isOpen = false">
              <router-link
                class="
                  flex
                  text-lg
                  items-center
                  p-4
                  hover:bg-blue-800
                  hover:text-white
                "
                to="/about"
                >About Us</router-link
              >
            </li>
            <li @click="isOpen = false">
              <router-link
                class="
                  flex
                  text-lg
                  items-center
                  p-4
                  hover:bg-blue-800
                  hover:text-white
                "
                to="/ourschool"
                >Our School</router-link
              >
            </li>

            <li @click="isOpen = false">
              <router-link
                class="
                  flex
                  text-lg
                  items-center
                  p-4
                  hover:bg-blue-800
                  hover:text-white
                "
                to="/gallery"
                >Gallery</router-link
              >
            </li>

            <li @click="isOpen = false">
              <router-link
                class="
                  flex
                  text-lg
                  items-center
                  p-4
                  hover:bg-blue-800
                  hover:text-white
                "
                to="/curriculum"
                >Curriculum</router-link
              >
            </li>

            <li v-if="regFormOpen" @click="isOpen = false">
              <a
                target="_blank"
                class="
                  flex
                  text-lg
                  items-center
                  p-4
                  hover:bg-blue-800
                  hover:text-white
                "
                :href="formUrl"
                >Register</a
              >
            </li>
            <li @click="isOpen = false">
              <router-link
                class="
                  flex
                  text-lg
                  items-center
                  p-4
                  hover:bg-blue-800
                  hover:text-white
                "
                to="/sponsors"
                >Sponsors</router-link
              >
            </li>
            <li @click="isOpen = false">
              <router-link
                class="
                  flex
                  text-lg
                  items-center
                  p-4
                  hover:bg-blue-800
                  hover:text-white
                "
                to="/team"
                >Team</router-link
              >
            </li>
          </ul>
        </aside>
      </div>
      <!-- App bar -->
      <div class="flex items-center pl-4">
        <a
          class="
            p-2
            text-white
            no-underline
            hover:no-underline
            text-2xl
            lg:text-2xl
          "
          href="/"
        >
          <img class="float-left pt-1" src="../assets/logo-sm.png" alt="Front-End Foxes School" />
          <span class="pt-1 pl-3">Front-End Foxes School</span>
        </a>
      </div>

      <div
        class="
          w-full
          flex-grow
          lg:flex
          lg:items-center
          lg:w-auto
          hidden
          p-4
          lg:p-0
          z-20
        "
        id="nav-content"
      >
        <ul class="list-reset lg:flex justify-end flex-1 items-center">
          <li class="hover:bg-blue-900">
            <router-link
              active-class="bg-blue-800"
              class="uppercase inline-block p-5 text-white no-underline"
              to="/about"
              >About Us</router-link
            >
          </li>
          <li class="hover:bg-blue-900">
            <router-link
              active-class="bg-blue-800"
              class="uppercase inline-block p-5 text-white no-underline"
              to="/ourschool"
              >Our School</router-link
            >
          </li>

          <li class="hover:bg-blue-900">
            <router-link
              active-class="bg-blue-800"
              class="uppercase inline-block p-5 text-white no-underline"
              to="/gallery"
              >Gallery</router-link
            >
          </li>

          <li class="hover:bg-blue-900">
            <router-link
              active-class="bg-blue-800"
              class="uppercase inline-block p-5 text-white no-underline"
              to="/curriculum"
              >Curriculum</router-link
            >
          </li>

          <li v-if="regFormOpen" class="hover:bg-blue-900">
            <a
              active-class="bg-blue-800"
              target="_blank"
              class="uppercase inline-block p-5 text-white no-underline"
              :href="formUrl"
              >Register</a
            >
          </li>
          <li class="hover:bg-blue-900">
            <router-link
              active-class="bg-blue-800"
              class="uppercase inline-block p-5 text-white no-underline"
              to="/sponsors"
              >Sponsors</router-link
            >
          </li>
          <li class="hover:bg-blue-900">
            <router-link
              active-class="bg-blue-800"
              class="uppercase inline-block p-5 text-white no-underline"
              to="/team"
              >Team</router-link
            >
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>
<script>
export default {

  data() {
    return {
      isOpen: false,
      regFormOpen: this.regFormOpen,
      formUrl: this.formUrl
    };
  },
  methods: {
    drawer() {
      this.isOpen = !this.isOpen;
    },
  },
  watch: {
    isOpen: {
      immediate: true,
      handler(isOpen) {
        if (process.client) {
          if (isOpen) document.body.style.setProperty("overflow", "hidden");
          else document.body.style.removeProperty("overflow");
        }
      },
    },
  },
  mounted() {
    document.addEventListener("keydown", (e) => {
      if (e.keyCode == 27 && this.isOpen) this.isOpen = false;
    });
  },
};
</script>
<style scoped>
ul li:hover > ul,
ul li ul:hover {
  visibility: visible;
  opacity: 1;
  display: block;
}
</style>
