<template>
  <div class="VPTeamPage">
    <slot />
  </div>
</template>

<style scoped>
.VPTeamPage {
  padding-bottom: 96px;
}

@media (min-width: 768px) {
  .VPTeamPage {
    padding-bottom: 128px;
  }
}

:slotted(.VPTeamMembers) {
  padding: 0 24px;
}

@media (min-width: 768px) {
  :slotted(.VPTeamMembers) {
    padding: 0 48px;
  }
}

@media (min-width: 960px) {
  :slotted(.VPTeamMembers) {
    padding: 0 64px;
  }
}
</style>
