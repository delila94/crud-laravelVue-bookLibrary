<template>
  <div>
    
   <nav class="bg-white px-8 pt-2 shadow-xl">
     <div class="-mb-px flex justify-center">
         <a class="no-underline text-teal-500 border-b-2 border-teal-dark uppercase tracking-wide font-bold text-xs py-3 mr-8" href="/">
             My library
         </a>
         <a class="no-underline text-grey-dark border-b-2 border-transparent uppercase tracking-wide font-bold text-xs py-3 mr-8" href="/create">
            Insert new book
         </a>
         <a class="no-underline text-grey-dark border-b-2 border-transparent uppercase tracking-wide font-bold text-xs py-3 mr-8" href="/view">
             View popular books
         </a>
     </div>
</nav>
  
    <transition name="fade">
      <router-view></router-view>
    </transition>
  </div>
</template>

<style>
    .fade-enter-active, .fade-leave-active {
      transition: opacity .5s
    }
    .fade-enter, .fade-leave-active {
      opacity: 0
    }
</style>

<script>

    export default{
    }
</script>