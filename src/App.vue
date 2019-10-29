<template>
  <div id="app">
      hello
      <tree-menu-wraper :treedata="JSON.stringify(treeData)"></tree-menu-wraper>
  </div>
</template>

<script>
var treeData = {
  name: "Group",
  children: [
    {
      name: "Sub Group",
      children: [{ name: "Group",
          children: [
              {
                  name:'<img class="joypixels" alt="😄" title=":smile:" src="https://cdn.jsdelivr.net/joypixels/assets/5.0/png/unicode/32/1f604.png"/> 1.9编程基础之顺序查找',
                  children:[{
                      name:'G5',
                      children:[
                          {
                              name:'item'
                          }
                      ]
                  }]

              }
          ]
      }, { name: "Item" }]
    },
    { name: "Item" ,password:true}
  ]
};
import treeMenuWraper from './treeMenuWraper.vue'
export default {
  name: 'app',
    data(){
        return {
            treeData
        }
    },
  components: {treeMenuWraper},
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
