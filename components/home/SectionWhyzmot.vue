<template>
  <section class="why-zmot bg-white pt-20">
    <div class="container mx-auto px-2 lg:px-4">
      <h2 class="text-center">
        {{ $t('homepage.why_do_you_need_ZMOT.header') }}
      </h2>
      <p class="text-center">
        {{ $t('homepage.why_do_you_need_ZMOT.text1') }}
        <strong>{{ $t('homepage.why_do_you_need_ZMOT.text2') }}</strong>
        {{ $t('homepage.why_do_you_need_ZMOT.text3') }}
        <strong>{{ $t('homepage.why_do_you_need_ZMOT.text4') }}</strong>
        {{ $t('homepage.why_do_you_need_ZMOT.text5') }}
      </p>
      <div class="feature__list mt-20">
        <div class="feature__item flex flex-wrap flex-col md:flex-row overflow-hidden pb-12" data-aos="fade-up" data-aos-delay="100" data-aos-once="true">
          <div class="my-3 px-3 lg:w-1/2 w-full overflow-hidden">
            <img
              :src="require('~/assets/img/why-do-you-need/searching_block.png').src"
              :srcset="require('~/assets/img/why-do-you-need/searching_block.png').srcSet"
              :blank-src="require('~/assets/img/why-do-you-need/searching_block.png').placeholder"
              alt="Why do you need Image"
            />
          </div>

          <div class="my-3 px-3 lg:w-1/2 w-full overflow-hidden">
            <div class="feature__item-content">
              <h3 class="my-8 font-bold text-center text-4xl">
                {{ $t('homepage.why_do_you_need_ZMOT.category_1_header') }}
              </h3>
              <p class="text-justify px-4">
                {{ $t('homepage.why_do_you_need_ZMOT.category_1_text') }}
              </p>
            </div>
          </div>
        </div>

        <div class="feature__item flex flex-wrap flex-col md:flex-row overflow-hidden pb-12" data-aos="fade-up" data-aos-delay="100" data-aos-once="true">
          <div class="my-3 px-3 lg:w-1/2 w-full overflow-hidden">
            <div class="feature__item-content text-right">
              <h3 class="my-8 font-bold text-center text-4xl">
                {{ $t('homepage.why_do_you_need_ZMOT.category_2_header') }}
              </h3>
              <p class="text-justify px-4">
                {{ $t('homepage.why_do_you_need_ZMOT.category_2_text') }}
              </p>
            </div>
          </div>
          <div class="my-3 px-3 lg:w-1/2 w-full overflow-hidden">
            <img
              :src="require('~/assets/img/why-do-you-need/service-mobile.png').src"
              :srcset="require('~/assets/img/why-do-you-need/service-mobile.png').srcSet"
              :blank-src="require('~/assets/img/why-do-you-need/service-mobile.png').placeholder"
              alt="Service Mobile Image"
            />
          </div>
        </div>

        <div class="feature__item flex flex-wrap flex-col md:flex-row overflow-hidden pb-12" data-aos="fade-up" data-aos-delay="100" data-aos-once="true">
          <div class="my-3 px-3 lg:w-1/2 w-full overflow-hidden">
            <img
              :src="require('~/assets/img/why-do-you-need/why_do_you_need_zmot-review.png').src"
              :srcset="require('~/assets/img/why-do-you-need/why_do_you_need_zmot-review.png').srcSet"
              :blank-src="require('~/assets/img/why-do-you-need/why_do_you_need_zmot-review.png').placeholder"
              alt="Why do you need zmot review Image"
            />
          </div>

          <div class="my-3 px-3 lg:w-1/2 w-full overflow-hidden">
            <div class="feature__item-content">
              <h3 class="my-8 font-bold text-center text-4xl">
                {{ $t('homepage.why_do_you_need_ZMOT.category_3_header') }}
              </h3>
              <p class="text-justify px-4">
                {{ $t('homepage.why_do_you_need_ZMOT.category_3_text') }}
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'SectionWhyzmot'
}
</script>

<style scoped lang="scss">
  @media (max-width: 768px) {
    section.why-zmot {
      .feature__list {
        .feature__item:nth-child(2n+1) {
          flex-direction: column;
        }
        .feature__item:nth-child(2n) {
          flex-direction: column-reverse;
          .feature__item-content {
            text-align: left !important;
          }
        }
      }
    }
  }
</style>
