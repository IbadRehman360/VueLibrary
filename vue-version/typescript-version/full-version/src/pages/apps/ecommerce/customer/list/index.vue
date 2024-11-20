<script setup lang="ts">
import ECommerceAddCustomerDrawer from '@/views/apps/ecommerce/ECommerceAddCustomerDrawer.vue';
import type { Customer } from '@db/apps/ecommerce/types';

const searchQuery = ref('')
const isAddCustomerDrawerOpen = ref(false)

// Data table options
const itemsPerPage = ref(10)
const page = ref(1)
const sortBy = ref()
const orderBy = ref()

// Data table Headers
const headers = [
  { title: 'Customer', key: 'customer' },
  { title: 'Customer Id', key: 'customerId' },
  { title: 'Country', key: 'country' },
  { title: 'Orders', key: 'orders' },
  { title: 'Total Spent', key: 'totalSpent' },
]

// Update data table options
const updateOptions = (options: any) => {
  sortBy.value = options.sortBy[0]?.key
  orderBy.value = options.sortBy[0]?.order
}

// Fetch customers Data
const { data: customerData } = await useApi<any>(createUrl('/apps/ecommerce/customers',
  {
    query: {
      q: searchQuery,
      itemsPerPage,
      page,
      sortBy,
      orderBy,
    },
  }),
)

const customers = computed((): Customer[] => customerData.value.customers)
const totalCustomers = computed(() => customerData.value.total)
</script>

<template>
  <div>
 
    <ECommerceAddCustomerDrawer v-model:is-drawer-open="isAddCustomerDrawerOpen" />
  </div>
</template>

<style lang="scss" scoped>
.customer-title:hover {
  color: rgba(var(--v-theme-primary)) !important;
}
</style>
