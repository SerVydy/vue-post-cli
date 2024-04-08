<template>
  <section id="form" >
    <form>
      <input type="text" v-model="title">
      <input type="text" v-model="body">
      <button class="btn" v-on:click.prevent="addPost" >Create</button>
    </form>
  </section>
  <section id="posts">
    <article v-for="post in posts" :key="post.id">
      <div>
        <p><b>Название:</b> {{ post.title }}</p>
        <p><b>Описание:</b> {{ post.body }}</p>
      </div>
      <button class="btn" v-on:click="removePost(post)">Delete</button>
    </article>
  </section>

</template>

<script>
  export default {
    data(){
      return{
        posts: [
          {id:1, title: 'JS1', body: 'JavaScript1'},
          {id:2, title: 'JS2', body: 'JavaScript2'},
          {id:3, title: 'JS3', body: 'JavaScript3'},
        ],
        title: '',
        body: '',
      }
    },
    methods:{
      addPost(){
        const post = {
          id: new Date().getTime(),
          title: this.title,
          body: this.body
        }
        this.posts.push(post)
        this.title = ""
        this.body = ""
      },
      removePost(post){
        this.posts = this.posts.filter(p => p.id !== post.id)
      }

    },
  }
</script>

<style>

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.btn{
  padding: 10px 20px;
  background-color: #fff;
  border: 1px solid teal;
  color: teal;
}

section{
  padding: 20px;
}

#form form{
  border: 2px solid teal;
  padding: 20px;
  display: grid;
  grid-template-rows: 40px 40px;
  row-gap: 10px;
}

#form button{
  justify-self: end;
}

#posts{
  display: grid;
  row-gap: 10px;
}

#posts article{
  border: 2px solid teal;
  padding: 20px;
  display: grid;
  grid-template-columns: 10fr 2fr;
}

#posts article div{
  display: grid;
  row-gap: 20px;
}

#posts article button{
  justify-self: end;
  align-self: center;
}

</style>
