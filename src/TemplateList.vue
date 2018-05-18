<template>
    <ul>
        <li v-for="(template, index) of templates" :key="index"> {{index}} </li>
    </ul>
</template>


<script>
export default {
    data() {
        return {
            templates: []
        }
    },

    methods:{
        save(){
            localStorage.setItem('templates', JSON.stringify(this.templates));
        },

        load(){
            this.templates = JSON.parse(localStorage.getItem('templates')) || [];
        }
    },

    created(){
        this.load();
    }
}
</script>

<style scoped>

</style>

