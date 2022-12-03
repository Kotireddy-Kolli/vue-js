<template>
    <div>
    <!-- Array of strings-->
    <h3 v-for="name in names" v-bind:key="name">{{name}}</h3>
    <h2>Render using index</h2>
    <h3 v-for="(name,index) in names" v-bind:key="index">{{index}}.{{name}}</h3>

    <!-- Array of Obj-->
    <h2>Render using Array of Obj</h2>
    <h3 v-for="name in objnames" :key="name.name">{{name.name}}</h3>

    <!-- Rendering Obj-->
    <h2>Render using Array of Obj</h2>
    <h3 v-for="(value,key,index) in greetings" :key="index">{{value}},{{key}},{{index}}</h3>

    <!-- Methods -->
    <h3>Multiple Method: {{multiply(2)}}</h3>
    </div>

</template>

<script>
export default {
    name: 'ListRender',
    data(){
        return {
            names: ['Hi','Hey','Hello'],
            objnames:[
                {name:'Hi'},
                {name:'Hey'},
                {name:'Hello'},
            ],
            greetings:{
                greeting1:"Hi",
                greeting2:"Hey",
                greeting3:'Hello'
            },
            baseMultiplier:5,
        }
    },
    methods:{
        multiply(num){
            return num*this.baseMultiplier
        }
    },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>