<template>
  <div>
    <DashboardHeader />
    <div class="px-2">
      <CommonTabs
        :tabs="navigationItems"
        :currentTab="currentTab"
        :wrapper-class="`relative mx-auto max-w-5xl`"
        :tab-class="`hover:bg-accent2 hover:rounded-md mx-2 my-2 p-2 text-sm`"
        :tab-active-class="`font-medium`"
        :line-class="`border-b border-b-2 border-geist-foreground `"
        @onClick="handleClick"
      />
    </div>

    <main class="border-t border-accent2">
      <Nuxt />
    </main>
    <CommonFooter />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  data() {
    return {
      navigationItems: [
        { title: 'Overview', value: '/' },
        // { title: 'Settings', value: 'settings' },
      ],
      currentTab: '/',
    }
  },
  methods: {
    handleClick(newTab: string) {
      if (newTab === '/') newTab = ''
      this.$router.push({ path: `/dashboard/${newTab}` })
    },
  },
})
</script>

<style>
#app {
  font-family: 'Inter', sans-serif;
}

.zi-input-group {
  height: 42px !important;
}
.zi-input-group.prefix input {
  height: 42px !important;
}

.zi-toggle {
  height: 20px !important;
  width: 40px !important;
}

.zi-toggle::before {
  height: 1rem !important;
  width: 1rem !important;
}

.zi-snippet > pre::before {
  content: '';
  user-select: none;
}

.zi-dialog-content {
  padding: 0 !important;
}
</style>
