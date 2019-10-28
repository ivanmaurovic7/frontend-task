<template>
    <div class="section section1">
        <div class="containerS1" :style="{transform: `translateY(-${this.section == 0 ? 0 : 25}vh)`}">
            <div class="textContentS1">
                <h1 id="Laborati-Ginori">Laborati Ginori</h1>
                <h4 class="UNIQUE-LUXURY">
                    <small class="EST-2018">EST {{year}}</small>
                    <br><span>UNIQUE LUXURY</span>
                </h4>
                <br>
                <h6>SCROLL DOWN</h6>
            </div>
        </div>
    </div>
</template>

<script>
import {TimelineLite, Back} from 'gsap'
import {SplitText} from 'gsap/SplitText'

export default {
    props: ['section'],
    
    data() {
        return {
            year: 1969,
            yearIncrementDelay: 0,
        }
    },

    methods: {
        increaseYearValue() {
            setTimeout(() => {
                this.yearIncrementDelay++
                this.year++
                if(this.year < 2018)
                    this.increaseYearValue()
            }, Math.exp(this.yearIncrementDelay/9))
        },
    },

    mounted() {
        setTimeout(() => {
            this.increaseYearValue()
        }, 600)

        // Letters animation
        let timeline =  new TimelineLite
        let mySplitText = new SplitText(`#Laborati-Ginori`, {type:"chars"})
        let chars = mySplitText.chars
        timeline.staggerFrom(chars, .35, {opacity:0, y:100, transformOrigin:"0% 50% -50",  ease:Back.ease}, .04, "+=0");
    }
}
</script>

<style lang="sass">
.section1
  background-color: #000000
  overflow: hidden
  transition: 1s ease
  .containerS1
    transition: 3s ease
    position: absolute
    left: 0
    right: 0
    top: 0
    bottom: 0
    width: 313px
    height: 83px
    margin: auto
    .textContentS1
        animation: slide-up-gently 3s ease-in-out forwards
        font-family: "PlainLight"
        font-size: 31.2px
        font-weight: normal
        font-stretch: normal
        font-style: normal
        letter-spacing: -0.59px
        text-align: center
        color: #ffffff
        #Laborati-Ginori
            overflow: hidden
            width: 313px
            height: 150px
            font-family: "PlainLight"
            font-size: 94px
            font-weight: normal
            font-stretch: normal
            font-style: normal
            line-height: 0.78
            letter-spacing: -5.49px
            color: #ffffff
            margin-bottom: 20px
            @media (max-width: 1300px)
                font-size: 50px
            @media (max-width: 1000px) and (orientation: landscape)
                height: 50px
        .UNIQUE-LUXURY
            width: 313px
            font-weight: normal
            font-stretch: normal
            font-style: normal
            animation: fade-in-top 1.5s ease forwards
        span
            display: block
            animation: fade-in-top-unique-luxury 1.5s ease forwards
        .EST-2018 
            font-family: "PlainLight"
            font-size: 22.2px
            letter-spacing: 2.58px
            color: #ffffff
        h6
            font-size: 12px
            word-spacing: 5px
            opacity: 0
            animation: fade-in-top 1.5s 5s ease forwards
            font-weight: normal
</style>