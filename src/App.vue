<template>
  <div id="app">
    <section1 :section="section"/>
    <section2 :section="section" :class="{sectionNotActive: (section < 1)}"/>
    <section3 :section="section" :class="{sectionNotActive: (section < 2)}"/>
  </div>
</template>

<script>
import section1 from './components/section1.vue'
import section2 from './components/section2.vue'
import section3 from './components/section3.vue'

export default {
  components: {
    section1,
    section2,
    section3
  },

  mounted() {
    // Used to get desired scrolling behaviour
    window.scrollBy(0, window.innerHeight*4)
    let lastScrollTop = 0
    setTimeout(() => {
      window.onscroll = () => {
        let st = window.pageYOffset || document.documentElement.scrollTop // Credits: "https://github.com/qeremy/so/blob/master/so.dom.js#L426"

          if (st > lastScrollTop){
              this.scrollTrigger(1)
          } else {
              this.scrollTrigger(-1)
          }

        lastScrollTop = st <= 0 ? 0 : st

      }
    }, 200)
  },

  methods: {
    // Used to get desired scrolling behaviour
    scrollTrigger(x) {
      if(!this.scrollInProgress) {
        this.scrollInProgress = true
        document.body.classList.add("scrollInProgress")

        if(x == 1 && this.section < document.querySelectorAll('.section').length - 1) {
          this.section += x
        }

        if(x == -1 && this.section > 0) {
          this.section += x
        }
        
        setTimeout(() => {
          this.scrollInProgress = false
          document.body.classList.remove("scrollInProgress")
      }, 1500)
      }
    }
  },

  data() {
    return {
      // Used to get desired scrolling behaviour
      scrollInProgress: false,
      section: 0,
    }
  }
}
</script>

<style lang="sass">
// Imports
@import './assets/fonts/Plain/PlainLight-Regular.css'
@import './assets/fonts/Plain/PlainBold-Regular.css' 


// General styling
*
  padding: 0
  margin: 0

#app 
  -webkit-font-smoothing: antialiased
  -moz-osx-font-smoothing: grayscale
  position: fixed
  width: 100vw
  height: 100vh

body 
  height: 1000vh
  overflow-x: hidden
  // Hide scrollbar
  -ms-overflow-style: none  // IE 10+
  scrollbar-width: none  // Firefox

body::-webkit-scrollbar
    display: none  // Safari and Chrome

.scrollInProgress
  overflow-y: hidden

.section
  width: 100vw
  height: 100vh
  transform: translateY(0)
  position: absolute

.sectionNotActive
  transform: translateY(100vh)

// Animations
@keyframes slide-up-gently
  from
    transform: translateY(0)
  to
    transform: translateY(-7vh)

@keyframes fade-in-top
  0%
    opacity: 0
    transform: translateY(200px)
  20%
    opacity: 0
    transform: translateY(200px)
  100%
    opacity: 1
    transform: translateY(0)

@keyframes fade-in-top-unique-luxury
  0%
    transform: translateY(150px)
    opacity: 0
  30%
    transform: translateY(150px)
    opacity: 0
  100%
    transform: translateY(0)
    opacity: 1

@keyframes animate-from-bottom
  0%
    transform: translateY(110%)
  55%
    transform: translateY(110%)
  100%
    transform: translateY(0)

@keyframes animate-to-top
  from
    transform: translateY(0)
  to
    transform: translateY(-180%)

</style>
