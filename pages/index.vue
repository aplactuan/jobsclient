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
import gql from 'graphql-tag';
import Job from "../components/Job";

export default {
  components: {Job},
  apollo: {
    jobs: {
      query: gql`
         {
          jobs(
            orderBy: [{column: CREATED_AT, order: DESC}],
         ) {
            id,
            job_title,
            job_location,
            job_link,
            company_name,
            company_logo,
            tags {
                title,
                slug
            }
          }
         }
      `,
      fetchPolicy: 'network-only'
    }
  }
}
</script>
