<template>
  <div v-if="!loading" class="container mx-auto px-2 lg:px-4">
    <div class="row flex flex-wrap">
      <div class="w-full header">
        <span> {{ $t("blog.opinion.title") }} </span>
      </div>
    </div>
    <div class="row flex flex-wrap">
      <div v-for="item of items" :key="item.id" class="w-full">
        <comment
          :comment="item"
          :replies="replies"
          :author="author"
          :post-id="postId"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CommentList',
  props: ['author', 'replies', 'postId'],
  data: () => ({
    loading: true,
    items: null
  }),
  mounted () {
    this.items = this.replies && this.replies.filter(reply => reply.parent === 0)
  },
  created () {
    this.$nextTick(function () {
      this.loading = false
    })
  }
}
</script>

<style lang="sass" scoped>
  .header
    font-size: 1.5em !important
    font-weight: 600 !important
    line-height: 1.8 !important
    margin: 20px 0
</style>
