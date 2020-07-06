
<template>
  <div class="w-full h-screen flex flex-col  items-center" >
<h5 class="text-3xl text-blue-800 m-3 " >Popular books to buy</h5> <br/>

    <img src="https://source.unsplash.com/random" class="h-64 w-full object-cover hidden sm:block">

  <div class="flex flex-col items-center bg-gray-400 w-2/3 p-10 rounded-lg shadow-xl -m-16" >
<img class="h-64  w-1/2 rounded-full" src="https://source.unsplash.com/random"/>
<h5 class="text-2xl font-semibold">Some image information</h5>
<p class="text-center mt-4"><span class="text-teal-900 font-extrabold"> ipsum dolor sit amet </span> consectetur adipisicing elit. Rem, placeat deleniti consequatur odit hic fugiat vitae laboriosam aliquid optio vel architecto excepturi molestiae sed. Dignissimos porro dolorem laudantium et quaerat!</p>
    </div>

  </div>
  
</template>

<script>
    export default {
        data () {
            return {
                name:null,author:null,img:null,errors:[],modalShow:false
                }

            },
        
        mounted() {
            console.log('Component mounted.')
        },
        
    }
</script>