<template>
    <div>
    <h3>{{name}}</h3>
    <div>
        <button v-on:click="name='Button name changed'">Change Name</button>
    </div>
    </div>
</template>

<script> 
export default {
    name: 'EventHandling',
    data(){
        return {
            name:'event'
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