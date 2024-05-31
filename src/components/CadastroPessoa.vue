<template>
    <div class="cadastro-pessoa">
      <h2>Cadastro de Pessoa</h2>
      <form @submit.prevent="submitForm" class="form">
        <div class="form-group">
          <label for="nome">Nome:</label>
          <input type="text" id="nome" v-model="localPessoa.nome" required>
        </div>
        <div class="form-group">
          <label for="idade">Idade:</label>
          <input type="number" id="idade" v-model="localPessoa.idade" required>
        </div>
        <div class="form-group">
          <label for="email">Email:</label>
          <input type="email" id="email" v-model="localPessoa.email" required>
        </div>
        <div class="form-group">
          <label for="habilidade">Habilidade:</label>
          <input type="text" id="habilidade" v-model="localPessoa.habilidade" required>
        </div>
        <button type="submit" class="btn">{{ editingIndex === null ? 'Adicionar Pessoa' : 'Salvar Edição' }}</button>
      </form>
    </div>
  </template>
  
  <script>
  import './CadastroPessoa.css';
  
  export default {
    props: {
      pessoa: Object,
      adicionarOuEditarPessoa: Function,
      editingIndex: Number
    },
    data() {
      return {
        localPessoa: { ...this.pessoa }
      };
    },
    watch: {
      pessoa(newPessoa) {
        this.localPessoa = { ...newPessoa };
      }
    },
    methods: {
      submitForm() {
        this.adicionarOuEditarPessoa(this.localPessoa);
      }
    }
  }
  </script>
  