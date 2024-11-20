<script lang="ts" setup>
import { useChatStore } from '@/views/apps/chat/useChatStore'
import type { ChatContact as TypeChatContact } from '@db/apps/chat/types'
import { useChat } from './useChat'

const props = defineProps<{
  search: string
  isDrawerOpen: boolean
}>()

const emit = defineEmits<{
  (e: 'openChatOfContact', id: TypeChatContact['id']): void
  (e: 'showUserProfile'): void
  (e: 'close'): void
  (e: 'update:search', value: string): void
}>()

const { resolveAvatarBadgeVariant } = useChat()
const search = useVModel(props, 'search', emit)

const store = useChatStore()
</script>

<template>
  
</template>

<style lang="scss">
.chat-contacts-list {
  --chat-content-spacing-x: 16px;

  padding-block-end: 0.75rem;

  .chat-contact-header {
    margin-block: 0.5rem 0.25rem;
  }

  .chat-contact-header,
  .no-chat-items-text {
    margin-inline: var(--chat-content-spacing-x);
  }
}

.chat-list-search {
  .v-field--focused {
    box-shadow: none !important;
  }
}
</style>
