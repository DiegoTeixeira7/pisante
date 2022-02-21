<template>
  <div>
    <nav class="tw-bg-white tw-shadow-lg">
      <div class="tw-max-w-6xl tw-mx-auto tw-px-4 height">
        <div class="tw-hidden lg:tw-flex tw-justify-between">
          <div class="tw-flex tw-space-x-7">
            <a href="/" class="tw-flex tw-items-center tw-py-4 tw-px-2">
              <span
                class="
                  text-body-medium text-body-medium
                  tw-text-black-light tw-ml-2
                "
                >Pisante</span
              >
            </a>
          </div>
          <!-- Right Navbar items -->
          <div class="tw-hidden md:tw-flex tw-items-center tw-space-x-3">
            <a href="/login" class="tw-ml-2 tw-px-2 btn background-hover">
              <span
                class="
                  text-body-medium text-body-medium
                  tw-text-black-light tw-ml-2
                "
                >Login</span
              >
            </a>
            <a class="tw-ml-2 tw-px-2 btn background-hover" href="/register">
              <span
                class="
                  text-body-medium text-body-medium
                  tw-text-black-light tw-ml-2
                "
                >Registrar</span
              >
            </a>
          </div>
        </div>
        <div class="lg:tw-hidden tw-flex tw-justify-between navbar-mobile-one">
          <!-- Mobile menu button -->
          <div class="tw-flex tw-items-center">
            <button class="tw-outline-none mobile-menu-button" @click="btn">
              <svg
                class="tw-w-6 tw-h-6 tw-text-gray-500"
                x-show="!showMenu"
                fill="none"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                viewBox="0 0 24 24"
                stroke="currentColor"
              >
                <path d="M4 6h16M4 12h16M4 18h16"></path>
              </svg>
            </button>
          </div>
          <div class="tw-flex tw-space-x-7">
            <a href="/" class="tw-flex tw-items-center tw-py-4 tw-px-2"> </a>
          </div>
        </div>
        <div class="tw-hidden navbar-mobile-two tw-mt-2 tw-pb-2">
          <!-- Mobile menu button -->
          <div class="tw-flex tw-justify-start tw-w-full">
            <div class="tw-flex tw-items-center">
              <button
                class="tw-outline-none navbar-mobile-two-prev"
                @click="btn3"
              >
                <svg
                  width="16"
                  height="16"
                  viewBox="0 0 16 16"
                  fill="none"
                  xmlns="http://www.w3.org/2000/svg"
                >
                  <path
                    d="M15 6.99997H3.82998L8.70998 2.11997C9.09998 1.72997 9.09998 1.08997 8.70998 0.699971C8.31998 0.309971 7.68998 0.309971 7.29998 0.699971L0.70998 7.28997C0.31998 7.67997 0.31998 8.30997 0.70998 8.69997L7.29998 15.29C7.68998 15.68 8.31998 15.68 8.70998 15.29C9.09998 14.9 9.09998 14.27 8.70998 13.88L3.82998 8.99997H15C15.55 8.99997 16 8.54997 16 7.99997C16 7.44997 15.55 6.99997 15 6.99997Z"
                    fill="black"
                  />
                </svg>
              </button>
            </div>
          </div>
        </div>
      </div>
    </nav>
    <!-- mobile menu -->
    <div
      class="
        mobile-menu
        tw-bg-white
        tw-shadow-lg
        tw-w-64
        tw-space-y-6
        tw-py-7
        tw-px-2
        tw-inset-y-0
        tw-left-0
        tw-transform
        tw-absolute
        tw--translate-x-full
        tw-transition
        tw-duration-200
        tw-ease-in-out
      "
    >
      <div class="tw-flex tw-mt-4">
        <button
          class="tw-ml-auto tw-outline-none mobile-menu-button-2"
          @click="btn2"
        >
          <svg
            class="tw-w-6 tw-h-6 tw-text-gray-500"
            x-show="!showMenu"
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M6 18L18 6M6 6l12 12"
            />
          </svg>
        </button>
      </div>
      <nav>
        <div class="tw-flex tw-flex-col tw-justify-start">
          <a href="/login" class="btn-2 background-hover">
            <span
              href="#"
              class="
                text-body-medium text-body-medium
                tw-text-black-light tw-ml-2
              "
              >Login</span
            >
          </a>
          <a href="/register" class="btn-2 background-hover tw-mt-2">
            <span
              class="
                text-body-medium text-body-medium
                tw-text-black-light tw-ml-2
              "
              >Registrar</span
            >
          </a>
        </div>
      </nav>
    </div>

    <Nuxt />
  </div>
</template>

<script>
export default {
  name: 'NavbarPage',
  data() {
    return {}
  },
  methods: {
    showSecondNavbar() {
      const firstNavbar = document.querySelector('.navbar-mobile-one')
      const secondNavbar = document.querySelector('.navbar-mobile-two')

      firstNavbar.classList.toggle('tw-hidden')
      secondNavbar.classList.toggle('tw-hidden')
    },
    btn() {
      const menu = document.querySelector('.mobile-menu')
      menu.classList.toggle('tw--translate-x-full')
    },
    btn2() {
      const menu = document.querySelector('.mobile-menu')
      menu.classList.toggle('tw--translate-x-full')
    },
    btn3() {
      this.showSecondNavbar()
    },
  },
}
</script>
<style>
</style>
