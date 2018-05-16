<template>
    <div>
        <div class="barcode-description">

        </div>

        <div class="barcode">
            <Barcode :value="value"/>
        </div>
    </div>
</template>

<script>
import Barcode from 'vue-barcode'

export default {
    title: "image",
    icon: '<svg enable-background="new 0 0 480 480" version="1.1" viewBox="0 0 480 480" xml:space="preserve" xmlns="http://www.w3.org/2000/svg"><path d="m80 48h-64c-8.832 0-16 7.168-16 16v64c0 8.832 7.168 16 16 16s16-7.168 16-16v-48h48c8.832 0 16-7.168 16-16s-7.168-16-16-16z"/>		<path d="m464 336c-8.832 0-16 7.168-16 16v48h-48c-8.832 0-16 7.168-16 16s7.168 16 16 16h64c8.832 0 16-7.168 16-16v-64c0-8.832-7.168-16-16-16z"/>		<path d="m464 48h-64c-8.832 0-16 7.168-16 16s7.168 16 16 16h48v48c0 8.832 7.168 16 16 16s16-7.168 16-16v-64c0-8.832-7.168-16-16-16z"/>		<path d="m80 400h-48v-48c0-8.832-7.168-16-16-16s-16 7.168-16 16v64c0 8.832 7.168 16 16 16h64c8.832 0 16-7.168 16-16s-7.168-16-16-16z"/>		<rect x="64" y="112" width="32" height="256"/>		<rect x="128" y="112" width="32" height="192"/>		<rect x="192" y="112" width="32" height="192"/>		<rect x="256" y="112" width="32" height="256"/>		<rect x="320" y="112" width="32" height="192"/>		<rect x="384" y="112" width="32" height="256"/>		<rect x="128" y="336" width="32" height="32"/>		<rect x="192" y="336" width="32" height="32"/>		<rect x="320" y="336" width="32" height="32"/></svg>',
    description: "Insert Barcode",

    props: ["options"],
    components: {
        Barcode
    },

    computed: {
        value(){
            return this.options.value
        }
    },

    methods: {

    },
}
</script>

