<style>
  dialog[open] {
  animation: appear .15s cubic-bezier(0, 1.8, 1, 1.8);
}

  dialog::backdrop {
    background: linear-gradient(45deg, rgba(0, 0, 0, 0.5), rgba(54, 54, 54, 0.5));
    backdrop-filter: blur(3px);
  }
  
 
@keyframes appear {
  from {
    opacity: 0;
    transform: translateX(-3rem);
  }

  to {
    opacity: 1;
    transform: translateX(0);
  }
} 
</style>
<template>
<div class="flex flex-wrap -mx-3 overflow-hidden sm:-mx-1 md:-mx-1">
      <div class="my-3 px-3 w-1/3 overflow-hidden sm:my-1 sm:px-1 md:my-1 md:px-1"  v-for="book in books" v-bind:key="book.id">
          <div class="p-4 max-w-xs bg-gray-400 shadow-xl  overflow-hidden rounded-lg"  >
            <div>
               <img class="rounded-full w-64 h-64 items-center mb-10 " v-bind:src="book.img" alt="montaña" />
            </div>
            <div class="p-3 space-y-3 items-center">
               <h3 class="text-gray-700 text-lg tracking-wide uppercase font-semibold text-md text-center">
                 {{book.name}}
               </h3>
               <p class=" text-gray-900 leading-sm text-center text-base">
                  {{book.author}}
               </p>
               <div class="items-center">
    <button onclick="document.getElementById('myModal').showModal()" @click="editBook(book.id)" class=" items-center py-2 px-10 shadow-md no-underline rounded-full bg-blue uppercase text-white font-sans font-semibold text-sm border-blue btn-primary hover:text-white hover:bg-blue-light focus:outline-none active:shadow-none mr-0">Edit</button>
    <button  @click="deleteBook(book.id)" class="shadow-md bg-red-700 right-0 text-white py-2 px-8 rounded-full uppercase font-semibold border-red-700 hover:text-white hover:bg-red-800">Delete</button>
            </div>
            </div>
      </div>
   </div>
   
<dialog id="myModal" class="h-auto w-11/12 md:w-1/2 p-5  bg-white rounded-md ">
        
   <div class="flex flex-col w-full h-auto ">
        <!-- Header -->
        <div class="flex w-full h-auto justify-center items-center">
          <div class="flex w-10/12 h-auto py-3 justify-center items-center text-2xl font-bold">
                Edit Book
          </div>
          <div onclick="document.getElementById('myModal').close();" class="flex w-1/12 h-auto justify-center cursor-pointer">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="#000000" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="feather feather-x"><line x1="18" y1="6" x2="6" y2="18"></line><line x1="6" y1="6" x2="18" y2="18"></line></svg>
          </div>
          <!--Header End-->
        </div>
          <!-- Modal Content-->
           <div class="flex w-full h-auto py-10 px-2 justify-center items-center  bg-blue-100 rounded text-center text-gray-900">
           <form >
            <div class="flex">
               <div class="w-1/3">
            <label>Name:</label>
             </div>
            <div class="w-2/3">
             <input  class=" bg-gray-200 px-4" v-model="book.name"/>
            </div>
             </div>
              <div class="flex">
            <div class="w-1/3">
            <label>Author:</label>
            </div>
             <div class="w-2/3">
             <input class=" bg-gray-200 px-4"  v-model="book.author"/>
            </div>
            </div>
             <div class="flex">
            <div class="w-1/3">
            <label>Img source:</label>
            </div>
            <div class="w-2/3">
             <input class=" bg-gray-200 px-4" v-model="book.img"/>
             </div>
            </div>
           
            <button @click="updateBook(book.id)"  class=" bg-indigo-700 m-3 p-2 rounded-full px-4 text-white hover:bg-indigo-500">Update Book</button>
            </form>
          </div>
          <!-- End of Modal Content-->
          
          
          
        </div>
</dialog>
 
   </div>
   
</template>

<script>
    //here will be shown all books
    export default {
        data(){
            return {
            books:[],
            book:{name:'',author:'',img:''},
            name:''
            }
            },
      //  mounted() { 
     //   },
        created(){
            axios.get('/api/books')
            .then(response=>{this.books=response.data});
            },
            methods:{
        deleteBook(id) {
                this.axios.delete('/api/book/delete/'+id)
                .then(response=>{this.$router.go() });
                },
        editBook(id) {
            this.axios.get('/api/book/edit/'+id)
            .then(response=>{this.book=response.data});

            },
            updateBook(id){

                this.axios.post('/api/book/update/'+id,this.book);

                },

        },
    }
</script>