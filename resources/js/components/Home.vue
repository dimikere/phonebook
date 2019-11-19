<template>
<div>
<nav class="panel column is-offset-2 is-8">
  <p class="panel-heading">
    Vue.js Phonebook App
    <button class="button is-link is-outlined " @click="openAdd">
      Add new
    </button>
  </p>
  <div class="panel-block">
    <p class="control has-icons-left">
      <input class="input" type="text" placeholder="Search">
      <span class="icon is-left">
        <i class="fas fa-search" aria-hidden="true"></i>
      </span>
    </p>
  </div>
  
  <a class="panel-block" v-for="item,key in lists">
    <span class="panel-icon">
      <i class="fa fa-book" aria-hidden="true"></i>
    </span>
    {{ item.name }}
    <span class="panel-icon column is-1">
      <i class="has-text-danger fa fa-trash" aria-hidden="true"></i>
    </span>
    <span class="panel-icon column is-1">
      <i class="has-text-info fa fa-edit" aria-hidden="true"></i>
    </span>
    <span class="panel-icon column is-1">
      <i class="has-text-primary fa fa-eye" aria-hidden="true" @click="openShow(key)"></i>
    </span>
  </a>
  <div class="panel-block">
    <button class="button is-link is-outlined is-fullwidth">
      Reset all filters
    </button>
  </div>
</nav>

<Add :openmodal='addActive' @closeRequest='close'></Add>
<Show :openmodal='showActive' @closeRequest='close'></Show>

</div>
</template>

<script>
let Add = require('./Add.vue').default;
let Show = require('./Show.vue').default;

export default {
  components: {Add, Show},
  data(){
    return{
      addActive : '',
      showActive: '',
      lists: {},
      errors: {}
    }
  },
  mounted(){
       axios.post('/getData')
       .then((response) => this.lists = response.data) 
       .catch((error) => console.log(error))
  },
  methods: {
    openAdd(){
      this.addActive = 'is-active';
    },
    openShow(key){
      this.$children[1].list = this.lists[key]
      this.showActive = 'is-active';
    },
    close(){
      this.addActive = this.showActive = '';
    }
  }

}
</script>