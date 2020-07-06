
<template>
  <div class="m-5 w-full h-screen">
<h1 class=" text-blue-800 flex justify-center text-4xl" >Create new Book</h1> <br/>
      <p v-if="errors.length">
    <b>Please correct the following error(s):</b>
    <ul>
      <li v-for="error in errors" v-bind:key="error">{{ error }}</li>
    </ul>
  </p>
  
<form class="w-full max-w-sm justify-center text-center shadow-xl p-5 px-16" @submit.prevent="createBook">
  <div class="md:flex md:items-center mb-6">
    <div class="md:w-1/3">
      <label class="block text-gray-800 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">
        Book Name
      </label>
    </div>
    <div class="md:w-2/3">
      <input v-model="name" class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-full-name" type="text" placeholder="Enter book name">
    </div>
  </div>
  <div class="md:flex md:items-center mb-6">
    <div class="md:w-1/3">
      <label class="block text-gray-800 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">
        Author Name
      </label>
    </div>
    <div class="md:w-2/3">
      <input v-model="author" class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-full-author" type="text" placeholder="Enter book author" >
    </div>
  </div>
  <div class="md:flex md:items-center mb-6">
    <div class="md:w-1/3">
      <label class="block text-gray-800 font-bold md:text-right mb-1 md:mb-0 pr-4" for="inline-full-name">
       Image Source
      </label>
    </div>
    <div class="md:w-2/3">
      <input v-model="img" class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-4 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500" id="inline-full-img" type="text" placeholder="Enter image source" >
    </div>
  </div>
  
  <div class="md:flex md:items-center">
    <div class="md:w-1/3"></div>
    <div class="md:w-2/3">
      <button class="shadow bg-purple-500 hover:bg-purple-400 focus:shadow-outline focus:outline-none text-white font-bold py-2 px-4 rounded" type="submit">
        Submit
      </button>
    </div>
  </div>
</form>

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
        //here will be possibility to add new book
        
            methods:{
                createBook(){
                    
    if(this.name!=null && this.author!=null && this.img!=null ){ //only if all data are valid
    this.axios.post('/api/book/add',{name:this.name,author:this.author,img:this.img})
    this.$router.push({name: 'home'});
     this.errors = [];
    }
      
      if(!this.name) this.errors.push("Name required."); //push in array
      if(!this.author) this.errors.push("Author required.");
      if(!this.img) this.errors.push("Image soruce required.");
  
    }

            },

    }
</script>