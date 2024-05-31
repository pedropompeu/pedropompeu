<template>
  <div class="formulario-pessoa">
    <CadastroPessoa
      :pessoa="pessoa"
      :adicionarOuEditarPessoa="adicionarOuEditarPessoa"
      :editingIndex="editingIndex"
    />
    <PessoasCadastradas
      :pessoas="pessoas"
      @editar-pessoa="editarPessoa"
      @deletar-pessoa="deletarPessoa"
    />
  </div>
</template>

<script>
import CadastroPessoa from './CadastroPessoa.vue';
import PessoasCadastradas from './PessoasCadastradas.vue';
import './FormularioPessoa.css';

export default {
  components: {
    CadastroPessoa,
    PessoasCadastradas
  },
  data() {
    return {
      pessoa: {
        nome: '',
        idade: null,
        email: '',
        habilidade: ''
      },
      pessoas: [],
      editingIndex: null
    };
  },
  methods: {
    adicionarOuEditarPessoa(pessoa) {
      if (this.editingIndex === null) {
        this.pessoas.push({ ...pessoa });
      } else {
        this.pessoas.splice(this.editingIndex, 1, { ...pessoa });
        this.editingIndex = null;
      }
      this.limparFormulario();
    },
    editarPessoa(index) {
      this.pessoa = { ...this.pessoas[index] };
      this.editingIndex = index;
    },
    deletarPessoa(index) {
      this.pessoas.splice(index, 1);
    },
    limparFormulario() {
      this.pessoa = {
        nome: '',
        idade: null,
        email: '',
        habilidade: ''
      };
    }
  }
}
</script>

