<template>
    <div class="component component--video">
        <div class="component__controls">
            <img src="/static/img/icons/close.svg" alt="Cerrar" @click="closeComponent()">
        </div>
        <div class="component__content">
            <span class="datestr" v-if="datum.datestr">{{datum.datestr}}</span>
            <h3>{{datum.title}}</h3>
            <p v-if="datum.desc">{{datum.desc}}</p>
            <div class="component__video">
                <iframe :src="datum.file" frameborder="0" allowfullscreen></iframe>
            </div>
        </div>
    </div>
</template>



<script>
import EventBus from '../plugins/bus'

export default {
    name: 'video-component',
    props: ['datum'],
    methods: {
        closeComponent(){
            EventBus.$emit('close-component')
        }
    },
}
</script>