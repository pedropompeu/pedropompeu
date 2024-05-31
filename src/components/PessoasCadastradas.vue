<template>
    <div class="pessoas-cadastradas">
      <h2>Pessoas Cadastradas</h2>
      <table class="pessoas-table">
        <thead>
          <tr>
            <th>Nome</th>
            <th>Idade</th>
            <th>Email</th>
            <th>Habilidade</th>
            <th>Ações</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(pessoa, index) in pessoas" :key="index">
            <td>{{ pessoa.nome }}</td>
            <td>{{ pessoa.idade }} anos</td>
            <td>{{ pessoa.email }}</td>
            <td>{{ pessoa.habilidade }}</td>
            <td>
              <div class="btn-group">
                <button @click="$emit('editar-pessoa', index)" class="btn editar">Editar</button>
                <button @click="$emit('deletar-pessoa', index)" class="btn deletar">Deletar</button>
              </div>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <script>
  import './PessoasCadastradas.css';
  
  export default {
    props: {
      pessoas: Array
    }
  }
  </script>
  