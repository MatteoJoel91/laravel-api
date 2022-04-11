<template>
  <main>
      <div class="container">
        <h1 class="my-4">Elenco dei post</h1>

        <div class="row">
            <div class="col-4 d-flex flex-wrap" v-for="post in posts" :key="post.id">
                <div class="card" style="width: 25rem;">
                    <div class="card-body">
                        <h5 class="card-title">{{post.title}}</h5>
                        <p class="card-text">{{post.content}}</p>
                        <a href="#" class="btn btn-primary">Vedi articolo intero</a>
                    </div>
                </div>
            </div>
        </div>
        
      </div>
      
  </main>
</template>

<script>
export default {
    name: 'Main',

    data(){
        return{
            posts: []
        }
    },

    methods: {
        getPosts() {
            axios.get('/api/posts').then((response)=>{
            console.log(response);
            this.posts = response.data.result;
        });
        }
    },

    created(){
        this.getPosts();
    },
}
</script>

<style>

</style>