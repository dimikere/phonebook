<template>
<nav class="panel column is-offset-2 is-8">
  <p class="panel-heading">
    Vue.js Phonebook App
    <button class="button is-link is-outlined ">
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
  
  <a class="panel-block">
    <span class="panel-icon">
      <i class="fas fa-book" aria-hidden="true"></i>
    </span>
    marksheet
    <span class="panel-icon">
      <i class="fa fa-trash" aria-hidden="true"></i>
    </span>
  </a>
  <div class="panel-block">
    <button class="button is-link is-outlined is-fullwidth">
      Reset all filters
    </button>
  </div>
</nav>
</template>