<template>
    <div class="hello">
        <h1>Welcome to administrator page - Admin</h1>
        <h2>{{msg}}</h2>
        <img src="../../img/w1200.jpg" :style="width" height="511" alt="Picture w1200"/>
        <h2>Ширина: {{width}}</h2>
    </div>
</template>

<script>
    export default {
        name: "Admin",
        data () {
            return {
                msg: 'The superheros'
            }
        },
        computed:{
            width(){
                switch (this.$vuetify.breakpoint.name) {
                    case 'xs':return {width:'335px', margin: '0 auto'};
                    case 'sm':return {width:'400px', margin: '0 auto'};
                    case 'md':return {width:'960px', margin: '0 auto'};
                    case 'lg':return {width:'1264px', margin: '0 auto'};
                    default:return {width:'768px', margin: '0 auto'};
                    // case 'sm':return '400px';
                    // case 'md':return '960px';
                    // case 'lg':return '1264px';
                    // default:return '768px';

                }
            }
        }
    }
</script>

<style scoped>
    h1, h2 {
        font-weight: normal;
    }
    ul {
        list-style-type: none;
        padding: 0;
    }
    li {
        display: inline-block;
        margin: 0 10px;
    }
    a {
        color: #42b983;
    }
</style>