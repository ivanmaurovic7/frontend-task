<template>
    <div class="section section2">
        <div class="navigation" :style="{transform: `translateY(${this.section == 1 ? 0 : -150}px)`, transitionDelay: section == 1 ? '2.25s' : '0s'}">
            <div class="linksGroup1">
                <a href="">ABOUT</a>
                <a href="">PRODUCTS</a>
            </div>
            <div class="linksGroup2">
                <a href="">TRADE</a>
                <a href="">CONTACT</a>
                <a href="" id="signIn">SIGN IN</a>
            </div>
        </div>
        <img src="@/assets/img/img0.png" :style="{transform: `rotateZ(${this.section == 1 ? 0 : 25}deg) translateY(${this.section == 2 ? -1200 : 0}px)`, transitionDelay: `${this.section == 1 ? 0.5 : 0}s`}">
        <img src="@/assets/img/img1.png" :style="{transform: `rotateZ(${this.section == 1 ? 0 : -20}deg) translateY(${this.section == 2 ? -1200 : 0}px)`, transitionDelay: `${this.section == 1 ? 0.5 : 0}s`}">
        <img src="@/assets/img/img2.png" :style="{transform: `rotateZ(${this.section == 1 ? 0 : 35}deg) translateY(${this.section == 2 ? -1200 : 0}px)`, transitionDelay: `${this.section == 1 ? 0.5 : 0}s`}">
        <div class="contentBeneath" :style="{transform: `scaleY(${this.section == 0 ? 0 : 1})`}">
        </div>
        <h1 id="Laborati-Ginori2" :style="{transform: `translateY(${this.section == 2 ? -700 : 0}px)`, opacity: section == 2 ? 0 : 1}">Laborati <br>Ginori</h1>
        <div class="EST-2018"><small :class="{animateFromBottom: section == 1, animateToTop: section == 2}">EST 2018</small></div>
        <div class="UNIQUE-LUXURY"><span :class="{animateFromBottom: section == 1, animateToTop: section == 2}">UNIQUE LUXURY</span></div>
    </div>
</template>

<script>
import {TimelineLite, Back} from 'gsap'
import {SplitText} from 'gsap/SplitText'

export default {
    props: ['section'],

    watch: {
        // Trigger when user scrolls to section two (letter animation)
        section() {
            if(this.section == 1) {
                new TimelineLite().staggerFrom(new SplitText(`#Laborati-Ginori2`, {type:"chars"}).chars, .7, {scale: .5, opacity:0, y:300, delay: 2, transformOrigin:"50% 0",  ease:Back.ease}, .04, "+=0")
            }
        }
    }
}
</script>

<style lang="sass">
.section2
    transition: 3s ease
    display: flex
    justify-content: center
    align-items: center
    position: relative
    overflow: hidden
    .navigation
        position: absolute
        transform-origin: top
        transition: .75s ease
        top: 0
        width: 100vw
        height: 70px
        z-index: 5
        display: flex
        justify-content: space-between
        align-items: center
        font-family: "PlainBold"
        @media (max-width: 900px)
            background: #fff
            height: 80px
            padding-bottom: 20px
            box-shadow: 0 0 20px rgb(120, 120, 120, .3)
        div
            margin: 0 50px
            a
                text-decoration: none
                margin: 0 20px
                color: #000000
            @media (min-width: 900px)
                #signIn
                    margin-left: 50px
        // I could build hamburger mobile menu, but don't have time
        @media (max-width: 900px)
            flex-direction: column
            div
                margin: 20px 0 0 0
                a
                    margin: 20px 10px 0 10px
    img
        width: 20vw
        transition: 3s ease
        position: relative
        z-index: 2
        opacity: .95
        @media (min-width: 1000px)
            &:nth-child(2)
                top: 5%
                right: 10%
            &:nth-child(3)
                bottom: 5%
                left: 5%
            &:nth-child(4)
                top: 10%
                left: 5%
    @media (max-width: 1000px) and (orientation: portrait)
        flex-direction: column
        img
            width: 50vw
            opacity: .9
            &:nth-child(2)
                margin-top: 50px
                
    .contentBeneath
        background-color: #f2f2f2
        width: 100vw
        height: 100vh
        position: absolute
        transition: 1s ease 1.5s
        transform-origin: bottom
    #Laborati-Ginori2
        overflow: hidden
        transition: 2s ease
        position: absolute
        z-index: 1
        left: 0
        right: 0
        top: 0
        bottom: 0
        margin: auto
        height: 35vw
        font-family: "PlainLight"
        font-size: 20vw
        letter-spacing: -22px
        @media (max-width: 1200px)
            font-size: 15vw
            letter-spacing: -12px
        @media (max-width: 1000px)
            letter-spacing: -5px
        @media (max-width: 1000px) and (orientation: landscape)
            top: 32vh
            font-size: 70px
        font-weight: normal
        font-stretch: normal
        font-style: normal
        line-height: 0.78
        text-align: center
        color: #000000
    span, small
        display: block
    .animateFromBottom
        animation: animate-from-bottom 4s ease forwards
    .animateToTop
        animation: animate-to-top 1.5s ease forwards
    .EST-2018 
        position: absolute
        bottom: 50px
        width: 193px
        font-family: "PlainLight"
        font-size: 25px
        font-weight: bold
        font-stretch: normal
        font-style: normal
        line-height: 3.73
        letter-spacing: 4.3px
        text-align: center
        color: #000000
        overflow: hidden
    .UNIQUE-LUXURY 
        position: absolute
        bottom: 15px
        width: 392px
        font-family: "PlainLight"
        font-size: 35px
        font-weight: normal
        font-stretch: normal
        font-style: normal
        line-height: 2.65
        letter-spacing: -0.98px
        text-align: center
        color: #000000
        overflow: hidden
        
</style>