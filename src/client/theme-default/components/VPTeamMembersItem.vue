<script setup lang="ts">
import type { DefaultTheme } from '..'
import VPIconHeart from './icons/VPIconHeart.vue'
import VPLink from './VPLink.vue'
import VPSocialLinks from './VPSocialLinks.vue'

defineProps<{
  member: DefaultTheme.TeamMember
}>()
</script>

<template>
  <article class="VPTeamMembersItem">
    <div class="profile">
      <figure class="avatar">
        <img class="avatar-img" :src="member.avatar" :alt="member.name">
      </figure>
      <h1 class="name">
        {{ member.name }}
      </h1>
      <p v-if="member.title || member.org" class="affiliation">
        <span v-if="member.title" class="title">
          {{ member.title }}
        </span>
        <span v-if="member.title && member.org" class="at">
          @
        </span>
        <VPLink v-if="member.org" class="org" :class="{ link: member.orgLink }" :href="member.orgLink" no-icon>
          {{ member.org }}
        </VPLink>
      </p>
      <p v-if="member.desc" class="desc">
        {{ member.desc }}
      </p>
      <div v-if="member.links" class="links">
        <VPSocialLinks :links="member.links" />
      </div>
    </div>
    <div v-if="member.sponsor" class="sponsor">
      <VPLink class="sponsor-link" :href="member.sponsor" no-icon>
        <VPIconHeart class="sponsor-icon" /> Sponsor
      </VPLink>
    </div>
  </article>
</template>

<style scoped>
.VPTeamMembersItem {
  display: flex;
  flex-direction: column;
  gap: 2px;
  border-radius: 12px;
  height: 100%;
  overflow: hidden;
}

.profile {
  flex-grow: 1;
  padding: 64px 32px;
  background-color: var(--vp-c-bg-soft);
}

.avatar {
  position: relative;
  margin: 0 auto;
  border-radius: 50%;
  width: 96px;
  height: 96px;
  box-shadow: var(--vp-shadow-3);
}

.avatar-img {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  border-radius: 50%;
  object-fit: cover;
}

.name {
  padding-top: 24px;
  text-align: center;
  letter-spacing: 0.15px;
  line-height: 28px;
  font-size: 20px;
  font-weight: 600;
}

.affiliation {
  padding-top: 2px;
  text-align: center;
  font-size: 16px;
  font-weight: 500;
  color: var(--vp-c-text-2);
}

.org.link {
  transition: color 0.25s;
}

.org.link:hover {
  color: var(--vp-c-brand);
}

.desc {
  margin: 0 auto;
  padding-top: 16px;
  max-width: 288px;
  text-align: center;
  font-size: 16px;
}

.links {
  display: flex;
  justify-content: center;
  margin: 0 -16px -8px;
  padding: 16px 12px 0;
  height: 56px;
}

.sponsor-link {
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  padding: 16px;
  font-size: 14px;
  font-weight: 500;
  color: var(--vp-c-sponsor);
  background-color: var(--vp-c-bg-soft);
  transition: color 0.25s, background-color 0.25s;
}

.sponsor-link:hover,
.sponsor-link:focus {
  outline: none;
  color: var(--vp-c-text-dark-1);
  background-color: var(--vp-c-sponsor);
}

.sponsor-icon {
  margin-right: 8px;
  width: 16px;
  height: 16px;
  fill: currentColor;
}
</style>
