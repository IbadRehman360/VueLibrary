<script lang="ts" setup>
import UserProfileHeader from '@/views/pages/user-profile/UserProfileHeader.vue'
import UserConnections from '@/views/pages/user-profile/connections/index.vue'
import UserProfile from '@/views/pages/user-profile/profile/index.vue'
import UserProjects from '@/views/pages/user-profile/projects/index.vue'
import UserTeam from '@/views/pages/user-profile/team/index.vue'

definePage({
  meta: {
    navActiveLink: 'pages-user-profile-tab',
    key: 'tab',
  },
})

const route = useRoute('pages-user-profile-tab')

const activeTab = computed({
  get: () => route.params.tab,
  set: () => route.params.tab,
})

// tabs
const tabs = [
  { title: 'Profile', icon: 'tabler-user-check', tab: 'profile' },
  { title: 'Team', icon: 'tabler-users', tab: 'teams' },
  { title: 'Projects', icon: 'tabler-layout-grid', tab: 'projects' },
  { title: 'Connections', icon: 'tabler-link', tab: 'connections' },
]
</script>

<template>
 
</template>
