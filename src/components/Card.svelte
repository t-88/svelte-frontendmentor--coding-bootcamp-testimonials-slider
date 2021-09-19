<div class="Card-comp" transition:scale>
    <section>
        <img class="background" src="../assets/pattern-quotes.svg" alt="text-background"/>
        <p class="text">{data.text}</p>
        <div class="user-data">
            <strong class="name">{data.name}</strong>
            <p class="jop">{data.jop}</p>
        </div>
    </section>
    <div class="img-container">
        <img class="user-img" src="../assets/{data.name}.jpg" alt="">
        <ArrowToggle on:arrow-clicked={ ({detail}) => {dispatch("arrow-clicked",detail)} }/>
        <img class="pattern-bg" src="./assets/pattern-bg.svg" alt="pattern-curve"> 
    </div>
</div>

<script>
	import ArrowToggle from "./ArrowToggle.svelte"
    import { createEventDispatcher } from "svelte"
    import { scale } from 'svelte/transition';
    
    const dispatch = createEventDispatcher()
    export let data;
</script>

<style type="text/scss">
    @import "../shared";
    .Card-comp {
        display: flex;
        position: absolute;
        .background {
            position: absolute;
        }
        section {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-self: center;
            position: relative;
            height: 360px;
        }
        .text {
            z-index: 1;
            font-weight: 300;
        }
        .user-data {
            display: flex;
            gap: 10px;
            p {
                color: hsl(240, 18%, 77%);
            }
        }
        .img-container {
            box-shadow: #000000b3 0 30px 40px -30px;
            align-self: center;
            position: relative;
            .user-img {
                width: 100%;
                border-radius: 5px;
            }
            .pattern-bg {
                position: absolute;
                z-index: -2;
            }

        }
        :global(.ArrowToggle-comp) {
            position: absolute;
            
        } 
    }
    @include media(">=650px") {
        $max-width: 1823;
        $min-width: 650;
        section {
            padding-left: applyMath(0,30,$max-width,$min-width);
            gap: applyMath(40,15,$max-width,$min-width);
            .background {
                width: applyMath(120,70,$max-width,$min-width);;
                top: applyMath(-30,70,$max-width,$min-width);;
                left: applyMath(100,75,$max-width,$min-width);;
            }
            .text {
                width: applyMath(750,365,$max-width,$min-width);
                font-size: applyMath(38,18,$max-width,$min-width);
            }
        }
        .user-data {
            font-size: applyMath(20,16,$max-width,$min-width);
        }
        .img-container {
            transform: translateX(applyMath(-75,-45,$max-width,$min-width));
            width: applyMath(540,270,$max-width,$min-width);
            height: applyMath(540,270,$max-width,$min-width);
            .pattern-bg {
                width: applyMath(697,350,$max-width,$min-width);
                bottom: applyMath(-52,-27,$max-width,$min-width);
                right: applyMath(-80,-39,$max-width,$min-width);
            }
        }
        :global(.ArrowToggle-comp) {
            width: applyMath(80,60,$max-width,$min-width) !important;
            height: applyMath(40,30,$max-width,$min-width) !important;
            padding: 0 applyMath(14,10,$max-width,$min-width) !important;
            bottom: applyMath(-19,-15,$max-width,$min-width);
            left: applyMath(93,25,$max-width,$min-width);
        }
    }
    @include media("<650px") {
        .Card-comp {
            flex-direction: column-reverse;
        }
        section {
            align-items: center;
            text-align: center;
            .background {
                $width: 70px;
                width: $width;
                left: calc(50% - #{$width} / 2)
            }
        }
        .user-data {
            flex-direction: column;
        }
        .img-container {
            transform: translateX(0);
        }
        :global(.ArrowToggle-comp) {
            :global(img) {
                width: 12px !important;
                height: 15px !important;
            }
        }
    }  
    @include media("<650px",">320px") {
        $max-width: 650;
        $min-width: 320;
        section {
            width: applyMath(490,301,$max-width,$min-width);
            gap: applyMath(30,20,$max-width,$min-width);
            .background {
                top: applyMath(40,70,$max-width,$min-width);
            }
            .text {
                font-size: applyMath(22,18,$max-width,$min-width);
            }
        }
        .user-data {
            font-size: applyMath(19,16,$max-width,$min-width);
        }
        .img-container {
            width: applyMath(340,270,$max-width,$min-width);
            height: applyMath(340,270,$max-width,$min-width);
            .pattern-bg {
                width: applyMath(438,350,$max-width,$min-width);
                bottom: applyMath(-33,-27,$max-width,$min-width);
                right: applyMath(-48,-39,$max-width,$min-width);
            }
        }
        :global(.ArrowToggle-comp) {
            $width: applyMath(80,75,$max-width,$min-width);
            $height: applyMath(40,40,$max-width,$min-width);
            width: $width !important;
            height: $height !important;
            bottom: calc(-1 * #{$height} / 2);
            left: calc(50% - #{$width} / 2);
            padding: 0 applyMath(12,14,$max-width,$min-width) !important;
        }
    }
    @include media("<=320px") {
        section {
            width: 301px;
            gap: 20px;
            .background {
                top: 70px;
            }
            .text {
                font-size: 18px;
            }
        }
        .user-data {
            font-size: 16px;
        }
        .img-container {
            width: 270px;
            height: 270px;
            .pattern-bg {
                width: 350px;
                bottom: -27px;
                right: -39px;
            }
        }
        :global(.ArrowToggle-comp) {
            $width: 75px;
            $height: 40px;
            width: $width !important;
            height: $height !important;
            bottom: calc(-1 * #{$height} / 2);
            left: calc(50% - #{$width} / 2);
            padding: 0 14px !important;
        }
    }  
</style>