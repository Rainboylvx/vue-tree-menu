<template>
<li :class="[model.password ?'password':'nopassword',isFolder ? 'folder' : 'file']">
    <label
      :class="{'open': open}"
      @click="toggle"
    >
      {{ model.name }}
      <div class="spaninfo">
          <div>
          <span class="input" v-if="dep===0">
              <input v-model="idata" type="text"  :disabled="idis" @keyup.enter="dealInput" ref="gain">
              <button @click="inputClick">S̶</button>
          </span>
          <span>
          </span>
          <span v-if="isFolder">{{ isFolder ? model.children.length : '' }}</span>
          </div>
      </div>
    </label>
    <ul v-show="open" v-if="isFolder" :class="{'open': open}">
      <tree-menu
        v-for="(model, index) in model.children"
        :key="index"
        :dep="dep+1"
        @childopen="handleChildopen"
        :model="model">
      </tree-menu>
    </ul>
  </li>
</template>

<script>
export default {
    name:'tree-menu',
    props: {
        model: Object,
        dep:{
            type:Number,
            default:0,
        }
    },
    data: function() {
        return {
            open: false,
            idis:true,
            idata:''
        };
    },
    computed: {
        isFolder: function() {
            return this.model.children && this.model.children.length;
        }
    },
    methods: {
        inputClick(e){
            this.idis = !this.idis
            e.cancelBubble = true;
            this.$nextTick( () =>{
                this.$refs.gain.focus()
            })
        },
        dealInput(){
            this.search(this.idata)
        },
        toggle: function() {
            if (this.isFolder) {
                this.open = !this.open;
            }
            else{
                window.location.href = this.model.url
            }
        },
        search(key){
            for( let c of this.$children){
                c.search(key)
            }
            if(this.model.name.indexOf(key)!==-1){
                this.$emit('childopen')
            }
        },
        handleChildopen(){
            this.open = true;
        }

    }
}
</script>

