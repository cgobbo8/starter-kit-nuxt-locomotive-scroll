<template>
  <LocomotiveScroll
    ref="scroller"
    :getted-options="{
      smooth: true,
      direction: 'vertical',
      smartphone: {
        smooth: true,
        direction: 'vertical',
      },
      tablet: {
        smooth: true,
        direction: 'vertical',
      },
    }"
  >
    <div class="example vertical">
      <header data-scroll-section>
        <h1>
          on Call<br />
          Function
        </h1>
      </header>
      <div class="example-section" data-scroll-section>
        <div class="example-content">
          <div
            class="example-big-square"
            data-scroll
            data-scroll-speed="-0.5"
          />
          <div
            class="example-small-square"
            data-scroll
            data-scroll-speed="2.5"
          />
        </div>
      </div>
      <div class="example-section" data-scroll-section>
        <div class="example-content">
          <div
            class="example-small-square"
            data-scroll
            data-scroll-speed="2.5"
          />
          <div
            class="example-big-square"
            data-scroll
            data-scroll-speed="-0.5"
          />
        </div>
      </div>
      <!-- Block with function -->
      <div class="example-section" data-scroll-section>
        <div class="example-fade-text" data-scroll data-scroll-call="fadeText">
          <h2>When I'm triggered... I disappear</h2>
        </div>
      </div>
      <!-- ./Block with function -->
      <div class="example-section" data-scroll-section>
        <div class="example-content">
          <div
            class="example-big-square"
            data-scroll
            data-scroll-speed="-0.5"
          />
          <div
            class="example-small-square"
            data-scroll
            data-scroll-call="callLog"
            data-scroll-speed="2.5"
          />
        </div>
      </div>
      <footer data-scroll-section>
        <nuxt-link to="/"> Go to Vertical Scroll </nuxt-link>
      </footer>
    </div>
  </LocomotiveScroll>
</template>

<script>
import gsap from 'gsap'

export default {
  mounted() {
    const locomotive = this.$refs.scroller.locomotive
    locomotive.on('scroll', (instance) => {
      const progress = (100 * instance.scroll.y) / instance.limit.y
      console.log(progress)
    })

    locomotive.on('call', (value, way, obj) => {
      switch (value) {
        case 'fadeText': {
          console.log(way)
          const child = obj.el.firstChild
          gsap.to(child, {
            duration: 2,
            ease: 'expo.out',
            opacity: 0.25,
          })
          break
        }
        case 'callLog': {
          console.log(way)
          gsap.to(obj.el, {
            duration: 2,
            ease: 'expo.out',
            scaleY: 0,
            opacity: 0.25,
            delay: 1,
          })
          break
        }
        default:
          break
      }
    })
  },
}
</script>

<style lang="scss">
@import './demo.scss';
</style>
