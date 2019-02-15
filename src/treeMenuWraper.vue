<style lang="scss">
@import "./treeMenu.scss"
</style>
<template>
<div>
    <div class="treeMenu-container">
        <ul class="cd-accordion-menu">
            <tree-menu :model="treeDataObj"></tree-menu>
        </ul>
    </div>
</div>
</template>
<script>
import treeMenu from './treeMenu.vue'
export default {
    data() {
        return {
        }
    },
    props:{
        treedata:String,
        default:'{}'
    },
    computed:{
        treeDataObj(){
            return JSON.parse(this.treedata)
        }
    },
    components:{
        treeMenu
    }
}
</script>
