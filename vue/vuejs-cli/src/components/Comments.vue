<template>
    <div class="container">
    <h1 class="header">Comentários</h1>
    <hr />
    <FormTodo v-on:add-todo="addComment"></FormTodo>
    <div class="list-group">
    <p v-if="comments.length <= 0">Sem comentários...</p>
    <div v-else class="list-group-item" v-for="(comment, index) in allComments" v-bind:key="index">
        <span class="comment__author">Autor: <strong>{{ comment.name }}</strong></span>
        <p>{{ comment.message }}</p>
        <div>
        <a href="#" title="Excluir" v-on:click.prevent="removeComment(index)">Excluir</a>
        </div>
    </div>
    </div>
    <hr />
  </div>
    
</template>

<script>
export default {
 
  data() {
    return {
      comments: []
    }
  },
  methods: {
    addComment(comment) {
      this.comments.push(comment);
    },
    removeComment(index) {
      this.comments.splice(index, 1);
    }
  },
  computed: {
    allComments() {
      return this.comments.map(comment => ({
        ...comment,
        name: comment.name.trim() === '' ? 'Anônimo' : comment.name
      }))
    }
  },
  watch: {
    comments(val) {
      console.log('val', val)
    }
  }
}
  

</script>


<style>
    body {
        background-color: #e1bee7;
    }

.alinhamento {
    margin-left: auto;
    margin-right: auto;
}

.header {
    width: 100%;
    height: 100px;
    color: white;
    font-family: Arial, Helvetica, sans-serif;
    font-size: 2.2em;
    text-align: center;
    padding-top: 20px;
    box-sizing: border-box;
    background-color: #5c007a;
}

main {
    width: 800px;
    min-height: 500px;
    height: auto;
    background-color: #ee98fb;
    text-align: center;
}

.list-group-item {
    margin-bottom: 10px;
}

footer {
    width: 100%;
    height: 50px;
    background-color: #5c007a;
    text-align: center;
    font-size: 1.5em;
    color: white;
    padding-top: 5px;
    box-sizing: border-box;
    text-decoration: none;
}

footer a {
    text-decoration: none;
    color: white;
    font-size: 1.2em;
}
</style>