<template>
  <div>
    <AdminNav />
    <main class="-mt-32">
      <div v-if="$route.meta.requiresProfile && !store.profile.username">
        <transition name="fade" mode="out-in">
          <OnboardingHero
            class="bg-white sm:rounded-lg mb-6 shadow max-w-5xl"
          />
        </transition>
      </div>
      <!-- Router Child -->
      <router-view class="h-full" v-slot="{ Component }">
        <transition name="fade" mode="out-in">
          <component :is="Component" />
        </transition>
      </router-view>
    </main>
    <!-- Footer -->
    <footer>
      <div class="mx-auto px-4 mb-14">
        <div class="text-xs text-gray-500 font-light text-center">
          <span class="block sm:inline"
            >&copy; 2021
            <a
              href="https://myairplane.io/"
              rel="noopener"
              target="_blank"
              aria-label="MyAirplane App"
              class="hover:text-primary-500"
              >MyAirplane™ App</a
            ></span
          >
          <span class="block sm:inline pl-1">All rights reserved.</span>
        </div>
      </div>
    </footer>
    <BetaBanner />
  </div>
</template>
<script>
import { store } from "../store";
import BetaBanner from "@/components/admin/local-chats/BetaBanner.vue";
import AdminNav from "../components/nav/AdminNav.vue";
import Breadcrumbs from "../components/nav/Breadcrumbs.vue";
import OnboardingHero from "@/components/admin/OnboardingHero.vue";

export default {
  components: {
    Breadcrumbs,
    OnboardingHero,
    BetaBanner,
    AdminNav,
  },
  setup() {
    return {
      store,
    };
  },
};
</script>