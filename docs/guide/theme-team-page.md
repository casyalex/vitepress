<script setup>
import { VPTeamMembers } from 'vitepress/theme'

const members = [
  {
    avatar: 'https://www.github.com/yyx990803.png',
    name: 'Evan You',
    title: 'Creator',
    links: [
      { icon: 'github', link: 'https://github.com/yyx990803' },
      { icon: 'twitter', link: 'https://twitter.com/youyuxi' }
    ]
  },
  {
    avatar: 'https://www.github.com/kiaking.png',
    name: 'Kia King Ishii',
    title: 'Developer',
    links: [
      { icon: 'github', link: 'https://github.com/kiaking' },
      { icon: 'twitter', link: 'https://twitter.com/KiaKing85' }
    ]
  }
]
</script>

# Team Page

If you would like to introduce your team, you may use Team components to construct the Team Page. There're 2 ways of using these components. One is to embbed it in doc page, and another is to create a full Team Page.

## Show team members in a page

You may use `<VPTeamMembers>` component exposed from `vitepress/theme` to display a list of team members on any page.

```html
<script setup>
import { VPTeamMembers } from 'vitepress/theme'

const members = [
  {
    avatar: 'https://www.github.com/yyx990803.png',
    name: 'Evan You',
    title: 'Creator',
    links: [
      { icon: 'github', link: 'https://github.com/yyx990803' },
      { icon: 'twitter', link: 'https://twitter.com/youyuxi' }
    ]
  },
  ...
]
</script>

# Our Team

Say hello to our awesome team.

<VPTeamMembers size="small" :members="members" />
```

The above will display a team member in card looking element. It should display something similar to below.

<VPTeamMembers size="small" :members="members" />

`<VPTeamMembers>` component comes in 2 different sizes, `small` and `medium`. While it boiles down to your preference, usually `small` size should fit better when used in doc page. Also, you may add more properties to each member such as adding "description" or "sponsor" button. Learn more about it in [`<VPTeamMembers>`](#vpteammembers).

Embbeding team members in doc page is good for small size team where having dedicated full team page might be too much, or introducing partial members as a refference to documenation context.

If you have large number of members, or simply would like to have more space to show team members, consider [creating a full team page](#create-a-full-team-page).

## Create a full Team Page

Instead of adding team members to doc page, you may also create a full Team Page, similar to how you can create a custom [Home Page](./theme-home-page).

To create a team page, first, create a new md file. The file name doesn't matter, but here lets call it `team.md`. In this file, set frontmatter option `layout: page`, and then you may compose your page structure using `TeamPage` components.

```html
---
layout: page
---
<script setup>
import {
  VPTeamPage,
  VPTeamPageTitle,
  VPTeamMembers
} from 'vitepress/theme'

const members = [
  {
    avatar: 'https://www.github.com/yyx990803.png',
    name: 'Evan You',
    title: 'Creator',
    links: [
      { icon: 'github', link: 'https://github.com/yyx990803' },
      { icon: 'twitter', link: 'https://twitter.com/youyuxi' }
    ]
  },
  ...
]
</script>

<VPTeamPage>
  <VPTeamPageTitle>
    <template #title>
      Our Team
    </template>
    <template #lead>
      The development of VitePress is guided by an international
      team, some of whom have chosen to be featured below.
    </template>
  </VPTeamPageTitle>
  <VPTeamMembers
    :members="members"
  />
</VPTeamPage>
```

When creating a full team page, remember to wrap all components with `<VPTeamPage>` component. This component will ensure all nested team related components gets the proper layout.

`<VPPageTitle>` component adds the page title section. The title being `<h1>` heading. Use `#title` and `lead` slot to document about your team.

`<VPMembers>` works as same as when used in a doc page. It will display list of members.

### Add sections to divide team members

## `<VPTeamMembers>`

## `<VPTeamPage>`

## `<VPTeamPageTitle>`

## `<VPTeamPageSection>`
