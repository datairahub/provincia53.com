<template>
    <g class="wave__wrap" transform="translate(-13, 20), scale(.5)">    
        <g id="wave">
            <path id="Line_1" d="M0.91,15L0.78,15A1,1,0,0,0,0,16v6a1,1,0,1,0,2,0s0,0,0,0V16a1,1,0,0,0-1-1H0.91Z"/>
            <path id="Line_2" d="M6.91,9L6.78,9A1,1,0,0,0,6,10V28a1,1,0,1,0,2,0s0,0,0,0V10A1,1,0,0,0,7,9H6.91Z"/>
            <path id="Line_3" d="M12.91,0L12.78,0A1,1,0,0,0,12,1V37a1,1,0,1,0,2,0s0,0,0,0V1a1,1,0,0,0-1-1H12.91Z"/>
            <path id="Line_4" d="M18.91,10l-0.12,0A1,1,0,0,0,18,11V27a1,1,0,1,0,2,0s0,0,0,0V11a1,1,0,0,0-1-1H18.91Z"/>
            <path id="Line_5" d="M24.91,15l-0.12,0A1,1,0,0,0,24,16v6a1,1,0,0,0,2,0s0,0,0,0V16a1,1,0,0,0-1-1H24.91Z"/>
            <path id="Line_6" d="M30.91,10l-0.12,0A1,1,0,0,0,30,11V27a1,1,0,1,0,2,0s0,0,0,0V11a1,1,0,0,0-1-1H30.91Z"/>
            <path id="Line_7" d="M36.91,0L36.78,0A1,1,0,0,0,36,1V37a1,1,0,1,0,2,0s0,0,0,0V1a1,1,0,0,0-1-1H36.91Z"/>
            <path id="Line_8" d="M42.91,9L42.78,9A1,1,0,0,0,42,10V28a1,1,0,1,0,2,0s0,0,0,0V10a1,1,0,0,0-1-1H42.91Z"/>
            <path id="Line_9" d="M48.91,15l-0.12,0A1,1,0,0,0,48,16v6a1,1,0,1,0,2,0s0,0,0,0V16a1,1,0,0,0-1-1H48.91Z"/>
        </g>
        <g class="wave__controls" @click="stopAudio()">
            <circle cx="26" cy="20" r="30"></circle>
            <g class="wave__stop">
                <rect x="15" y="7" width="9" height="26"></rect>
                <rect x="29" y="7" width="9" height="26"></rect>
            </g>
        </g>
    </g>
</template>



<script>
import EventBus from '../plugins/bus'
export default {
    name: 'svg-wave',
    methods: {
        stopAudio(){
            EventBus.$emit('stop-audio')
        }
    },
}
</script>



<style lang="scss">
#wave {
    height: 70px;
    width: 70px;
    fill: #fff;
    path {
        transform-origin: 0 14px;
    }
}

.wave {
    &__controls {
        cursor: pointer;
        display: none;
        circle {
            fill: #050505;
            stroke: white;
        }
        rect {
            fill: white;
        }
    }
    &__wrap:hover {
        .wave__controls {
            display: block;
        }
    }
}

@for $i from 1 through 9 {
    #Line_#{$i} {
        animation: pulse 1s infinite;
        animation-delay: $i * .15s;
    }
}

@keyframes pulse {
    0% {
        transform: scaleY(1);
    }
    50% {
        transform: scaleY(.7);
    }
    100% {
        transform: scaleY(1);
    }
}
</style>