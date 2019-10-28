<template>
    <div class="section section3">
        <div class="introduction">
            <small>Introduction</small>
        </div>
        <div class="crete">
            <span id="crete">Crete was created by to bring excellence in furniture design and creat something new, simply different and very own, very characteristic.</span>
        </div>
        <div class="img" :style="{transform: `scale(${this.section == 2 ? 1 : 1.5}) translateY(${this.section == 2 ? 0 : 200}px)`, opacity: section == 2 ? 1 : 0}"><img src="@/assets/img/img3.png" alt=""></div>
        <div class="turbine-lamp">
            <span class="An-elegant-floor-lam" id="elegant-floor-lam" :style="{opacity: section == 2 ? 1 : 0}">
                An elegant floor lamp with a sophisticated and contemporary design.
            </span>
            <h2 class="Turbine-lamp" id="turbine-lam">
                Turbine Lamp
            </h2>
            <p class="Contains-several-com" id="contains-several">
                Contains several components that expand from its center containing specific lamps and carefully positioned to be able to project light through the salience of the part. 
            </p>
        </div>
        <div class="arrow" :style="{transform: `scale(${this.section == 2 ? 1 : 1.5}) translateY(${this.section == 2 ? 0 : 70}px)`, opacity: section == 2 ? 1 : 0}">
            <img src="@/assets/img/arrow.png" alt="">
        </div>
        <div class="paging">
            <span>01/04</span>
        </div>
    </div>
</template>

<script>
import {TimelineLite, Back} from 'gsap'
import {SplitText} from 'gsap/SplitText'

export default {
   props: ['section'],

    watch: {
        section() {
            // Trigger when user scrolls to section three (letter animation)
            if(this.section == 2) {
                new TimelineLite().staggerFrom(new SplitText(`#crete`, {type:"words"}).words, 2.5, {opacity:0, y:5, delay: .5, transformOrigin:"50% 0",  ease:Back.ease}, .04, "+=0")

                new TimelineLite().staggerFrom(new SplitText(`#turbine-lam`, {type:"words"}).words, 1, {opacity:0, y:5, delay: 2.15, transformOrigin:"50% 0",  ease:Back.ease}, .015, "+=0")

                new TimelineLite().staggerFrom(new SplitText(`#contains-several`, {type:"words"}).words, 1, {opacity:0, y:5, delay: 2.15, transformOrigin:"50% 0",  ease:Back.ease}, .035, "+=0")
            }
        }
    }
}
</script>

<style lang="sass">
.section3
    width: 100vw
    height: 100vh
    transition: 2.2s ease
    background: #f2f2f2
    display: grid
    grid-template-columns: 3fr 2fr 2fr
    grid-template-rows: 3fr 3fr 4fr
    grid-template-areas: "intro crete crete" "img turbine paging" "img turbine arr"
    @media (max-width: 1300px)
        grid-template-areas: "img img img" "turbine turbine turbine" "paging arr arr"
        .crete, .intro
            display: none
    @media (max-width: 1000px) and (orientation: landscape)
        grid-template-areas: "img turbine turbine" "img turbine turbine" "arr arr arr"

.introduction
    grid-area: intro
    small
        display: block
        position: relative
        top: 75px
        left: 200px
        width: 83px
        height: 31px
        transform: rotate(-90deg)
        font-family: "PlainBold"
        font-size: 15px
        font-stretch: normal
        font-style: normal
        line-height: 2.07
        letter-spacing: -0.28px
        color: #000000

.crete
    grid-area: crete
    padding: 1vw 3vw
    span
        width: 740px
        height: 283px
        font-family: "PlainLight"
        font-size: 45px
        font-weight: 300
        font-stretch: normal
        font-style: normal
        line-height: 1.18
        letter-spacing: -0.85px
        color: #000000
        text-transform: uppercase

.img
    grid-area: img
    padding: 5%
    transition: 1s 1.5s ease
    img
        width: 100%
        height: 100%
        @media (max-width: 1300px)
            width: 300px
            height: auto
        @media (max-width: 350px)
            width: 200px

.turbine-lamp
    grid-area: turbine
    padding: 3vw
    .An-elegant-floor-lam
        transition: 1s 2s ease
        border-left: 1px solid #000000
        padding-left: 10px
        margin-left: 10px
        display: block
        width: 222px
        height: 34px
        font-family: "PlainLight"
        font-size: 12px
        font-weight: normal
        font-stretch: normal
        font-style: normal
        line-height: 1.42
        letter-spacing: -0.23px
        color: #000000
    .Turbine-lamp
        margin-top: 2vw
        width: 455px
        height: 70px
        font-family: "PlainLight"
        font-size: 76px
        font-weight: normal
        font-stretch: normal
        font-style: normal
        line-height: 0.92
        letter-spacing: -2.34px
        text-align: center
        color: #000000
    .Contains-several-com 
        margin: 30px 0 0 10px
        width: 496px
        height: 175px
        font-family: "PlainLight"
        font-size: 25px
        font-weight: 300
        font-stretch: normal
        font-style: normal
        line-height: 1.4
        letter-spacing: -0.47px
        color: #000000
    @media (max-width: 1300px)
        .Turbine-lamp
            height: auto
            font-size: 35px
            text-align: left
            margin: 20px 0 10px 5px
        .Contains-several-com 
            margin-top: 0
            font-size: 15px
            width: 90vw
    @media (max-width: 1000px) and (orientation: landscape)
        .Contains-several-com 
            width: 35vw

.paging
    grid-area: paging
    position: relative
    span
        position: absolute
        right: 100px
        top: 50px
        font-family: "PlainLight"
        display: block
        transform: rotateZ(-90deg)
        @media (max-width: 1300px)
            top: -35px
            right: 0

// Could use lottie to make svg animation like in video, but didn't have time
.arrow
    grid-area: arr
    position: relative
    transition: 1s 3s ease
    img
        position: absolute
        left: 0
        top: 0
        right: 0
        bottom: 0
        margin: auto
        width: 150px
        height: 150px
        @media (max-width: 1300px)
            width: 60px
            height: 60px
            left: 25vw
            bottom: 45px
        @media (max-width: 1000px) and (orientation: landscape)
            right: -70px
            bottom: -50px
        transition: .5s ease
        &:hover
            cursor: pointer
            transform: scale(1.1)
</style>