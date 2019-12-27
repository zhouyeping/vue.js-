<template>
  <div>
  <li id="special_li">This is a unique li element</li>
  <ul>
    <li>first</li>
    <li>second</li>
    <li>third</li>
  </ul>
  <div class="parent">
    <div class="child"></div>
  </div>

  </div>
</template>

<script>
    export default {
        name: "SecondComponent"
    }
</script>

<style scoped>
  #special_li{

  }
  li{
    background-color: lightblue;
    border: 1px solid black;
  }
  ul{
    background-color: lightyellow;
    padding: 0px;
    display: inline-block;
  }
  ul li {
    list-style-type: none;
    display: inline-block;
  }
  div.parent{
    width: 200px;
    height: 200px;
    background-color: lightgray;
  }
  div.child{
    background-color: cyan;
  }
</style>
