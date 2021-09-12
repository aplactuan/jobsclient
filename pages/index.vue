<template>
  <div>
    <div class="py-10 text-center">
      <h1 class="text-4xl font-bold mb-2">The best jobs available for you</h1>
      <p class="font-medium text-gray-400">Find the best jobs available for you</p>
    </div>

    <div class="mt-10">
      <Job v-for="job in jobs" :key="job.id" :job="job" />
    </div>
  </div>
</template>

<script>
import ALL_TAGS from '@/graphql/AllJobs.gql'

export default {
  apollo: {
    jobs: {
      query: ALL_TAGS,
      fetchPolicy: 'network-only'
    }
  }
}
</script>
