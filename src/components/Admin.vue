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
                switch (screen.width) {
                    case 375  :return {width:'358px', height: 'auto', margin: '0 auto'};
                    case 414  :return {width:'397px', height: 'auto', margin: '0 auto'};
                    case 1024 :return {width:'768px', height: 'auto', margin: '0 auto'};
                    case 1920 :return {width:'768px', height: 'auto', margin: '0 auto'};
                    default   :return {width: document.body.clientWidth+'px', height: 'auto', margin: '0 auto'};
                    // case 'sm':return '400px';
                    // case 'md':return '960px';
                    // case 'lg':return '1264px';
                    // default:return '768px';

                }
            }
        },
        created() {
            let width = document.body.clientWidth, // ширина
            // widthDiv = document.div.clientWidth, // ширина
            height = document.body.clientHeight; // высота
            console.log('Ширина экрана screen.width:', screen.width); //375
            // console.log('Ширина экрана widthDiv:', widthDiv); //375
            console.log('Ширина экрана width :', width); //359
            console.log('Высота экрана width :', height);

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