<template>

<div>
  <div>First Name:{{firstname}}</div>
  <!-- <div v-text="lastname">Lastname:</div> //Throw an error-->
  <div v-text="lastname"></div>
  <div >Lastname:{{boldlastname}}</div>
  <div v-html="boldlastname"></div>

  <!-- Binding Attributes--->
  <h3 v-bind:id="heading">Heading h3</h3>
  <button v-bind:disabled="isDisabled">Bind</button>

  <!-- Binding Static Classes-->
  <div class="underlined">This Text Shoud be underlined</div>

  <!-- Binding Dynamic Classes-->
  <div v-bind:class="status">Color change Based on status </div>

  <!-- Binding Styles-->

  <h2 v-bind:style="{
    color: highlightColor,
    fontSize: headerSize+ 'px',
    padding:'20px',
  }">Inline Styles</h2>
  </div>
</template>

<script>


export default {
  name: 'App',
  data(){
    return {
      firstname: "Koti",
      lastname: "Reddy",
      boldlastname: "<b>Reddy</b>",
      heading: "heading",
      isDisabled: false,
      status:"accepted",
      highlightColor:"Blue",
      headerSize:50,
    };
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
.underlined{
  text-decoration: underline;
}
.accepted{
  color: green;
}
.rejected{
  color: red;
}
</style>
