<template>
  <div>
    <div v-if="!isLoading" class="container mx-auto px-2 lg:px-4">
      <section v-if="!!totalNum" id="blogs" class="blogs my-20 lg:m-20">
        <nuxt-link
          v-for="post of pageOfItems"
          id="blog-card"
          :key="post.id"
          :to="localePath({
            name: 'blog-slug',
            params: { slug: post.slug }
          })"
          class="blog--item no-underline"
          data-aos="fade-up"
        >
          <div class="card overflow-hidden">
            <div class="row flex flex-wrap">
              <div class="w-full md:w-1/3">
                <img :src="post._embedded['wp:featuredmedia'][0].media_details.sizes.medium.source_url" alt="Post Image" class="rounded-none" />
              </div>
              <div class="w-full md:w-2/3">
                <div class="card-body">
                  <div class="card-title text-white bg-primary text-2xl mb-3 font-medium">
                    {{ post.title.rendered }}
                  </div>
                  <div class="card-text" v-html="post.excerpt.rendered" />
                  <!-- <div class="card-meta">
                    Mais de 2.000 profissionais de marketing já leram esse conteúdo
                  </div> -->
                </div>
              </div>
            </div>
          </div>
        </nuxt-link>
        <client-only>
          <div class="text-center pagination">
            <jw-pagination
              :items="posts"
              :labels="customLabels"
              :styles="customStyles"
              :page-size="5"
              @changePage="gotoPage"
            />
          </div>
        </client-only>
      </section>

      <section v-else id="blog" class="blog pt-20 m-20">
        No blogs detected
      </section>
    </div>
    <div v-else class="container mx-auto min-h-80">
      <loading
        :active.sync="isLoading"
        :can-cancel="false"
        :is-full-page="fullPage"
        :color="color"
      />
    </div>
  </div>
</template>

<script>
import JwPagination from 'jw-vue-pagination'
export default {
  name: 'SectionBlog',
  components: { JwPagination },
  async fetch () {
    this.isLoading = true
    try {
      const result = await this.$axios.get('https://thezmot.com/wp-json/wp/v2/posts?_embed=1')
      this.totalNum = result.data.length
      this.posts = result &&
        result.data &&
        result.data.sort((post1, post2) => {
          const post1Date = new Date(post1.date_gmt)
          const post2Date = new Date(post2.date_gmt)

          if (post1Date - post2Date > 0) {
            return -1
          } else {
            return 1
          }
        })
    } catch (e) {
      this.posts = []
      this.totalNum = 0
    } finally {
      this.isLoading = false
    }
    /* this.isLoading = true
    try {
      const result = await this.$axios.get('https://thezmot.com/wp-json/wp/v2/posts')
      this.totalNum = result.data.length
      this.isLoading = false
    } catch (e) {
      this.totalNum = 0
      this.isLoading = false
    } finally {
      this.initializeBlogContents()
    } */
  },
  data: () => ({
    rows: 100,
    currentPage: 0,
    totalNum: 0,
    posts: [],
    pageOfItems: [],
    baseUrl: 'https://thezmot.com/wp-json/wp/v2/',
    perPage: 9,
    pages: [],
    fullPage: true,
    isLoading: true,
    color: '#ff6600',
    customLabels: {
      first: '«',
      last: '»',
      previous: '‹',
      next: '›'
    },
    customStyles: {
      li: {
      },
      a: {
        color: '#fc642e',
        margin: '0 .8rem',
        padding: '.3rem 1rem',
        'border-radius': '5px'
      }
    }
  }),
  watch: {
    '$route.query.page' (value) {
      this.currentPage = value
    }
  },
  methods: {
    linkGen (pageNum) {
      return pageNum === 1 ? '?page=1' : `?page=${pageNum}`
    },
    gotoPage (pageItems) {
      this.pageOfItems = pageItems
      // this.$fetch()
    }
  }
}
</script>

<style scoped lang="scss">

</style>
