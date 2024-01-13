<template>
  <header class="sticky top-0 bg-weather-primary shadow-lg">
    <nav
      class="container flex flex-nowrap flex-col sm:flex-row items-center gap-4 text-white py-6"
    >
      <RouterLink :to="{ name: 'home' }">
        <div class="flex items-center gap-3">
          <i class="fa-solid fa-sun text-2xl"></i>
          <p class="text-2xl">The Local Weather</p>
        </div>
      </RouterLink>

      <div class="icon flex gap-3 flex-1 justify-end">
        <i
          @click="toggleModal"
          class="fa-solid fa-circle-info text-xl cursor-pointer text-white hover:text-weather-secondry duration-150"
        ></i>
        <i class="fa-solid fa-plus text-xl cursor-pointer text-white"></i>
      </div>
      <teleport to="body">
        <transition name="modal-outer">
          <BaseModal v-if="modalActive" :toggle-modal="toggleModal">
            <transition name="modal-inner">
              <div class="text-black" v-if="show">
                <h1 class="text-2xl mb-1">About:</h1>
                <p class="mb-4">
                  The Local Weather allows you to track the current and future
                  weather of cities of your choosing.
                </p>
                <h2 class="text-2xl">How it works:</h2>
                <ol class="list-decimal list-inside mb-4">
                  <li>
                    Search for your city by entering the name into the search bar.
                  </li>
                  <li>
                    Select a city within the results, this will take you to the
                    current weather for your selection.
                  </li>
                  <li>
                    Track the city by clicking on the "+" icon in the top right.
                    This will save the city to view at a later time on the home
                    page.
                  </li>
                </ol>
                <h2 class="text-2xl">Removing a city</h2>
                <p>
                  If you no longer wish to track a city, simply select the city
                  within the home page. At the bottom of the page, there will be
                  am option to delete the city.
                </p>
              </div>
            </transition>
          </BaseModal>
        </transition>
      </teleport>
    </nav>
  </header>
</template>

<script>
import { RouterLink } from "vue-router";
import BaseModal from "./BaseModal.vue";
export default {
  name: "SiteNavigation",
  components: {
    BaseModal,
  },
  data() {
    return {
      modalActive: false,
      show: false,
    };
  },
  methods: {
    toggleModal: function () {
      this.modalActive = !this.modalActive;
      this.show = !this.show;
    },
  },
};
</script>
<style>
.modal-outer-enter-active,
.modal-outer-leave-active {
  transition: opacity 0.5s ease;
}

.modal-outer-enter-from,
.modal-outer-leave-to {
  opacity: 0;
}
.modal-inner-enter-active,
.modal-inner-leave-active {
  transition: opacity 0.5s ease;
}

.modal-inner-enter-from,
.modal-inner-leave-to {
  opacity: 0;
}
</style>
