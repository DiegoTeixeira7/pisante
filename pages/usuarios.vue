<template>
  <div class="tw-m-8 tw-flex tw-flex-col">
    <div
      class="
        tw-mt-4 tw-w-full tw-grid tw-gris-cols-1
        lg:tw-grid-cols-3
        tw-justify-items-center tw-gap-2
      "
    >
      <div v-for="(user, index) in users" :key="index">
        <list-users :user="user" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios, error }) {
    let data = []
    await $axios
      .get('/api/public_html/api/user/')
      .then((res) => {
        data = res?.data?.data
      })
      .catch()
    return { users: data }
  },
}
</script>

<style>
</style>
