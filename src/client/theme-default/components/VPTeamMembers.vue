<script setup lang="ts">
import type { DefaultTheme } from '..'
import VPTeamMembersItem from './VPTeamMembersItem.vue'

defineProps<{
  members: DefaultTheme.TeamMember[]
}>()
</script>

<template>
  <div class="VPTeamMembers">
    <div class="container">
      <div v-for="member in members" :key="member.name" class="item">
        <VPTeamMembersItem :member="member" />
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: grid;
  gap: 24px;
  grid-template-columns: repeat(auto-fit, minmax(256px, 1fr));
  margin: 0 auto;
  max-width: 1152px;
}

@media (min-width: 372px) {
  .container {
    grid-template-columns: repeat(auto-fit, minmax(288px, 1fr));
  }
}
</style>
