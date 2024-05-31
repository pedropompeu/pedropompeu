<template>
  <div id="app">
    <header>
      <h1>Cadastro de Pessoas</h1>
    </header>
    <main>
      <FormularioPessoa />
    </main>
  </div>
</template>

<script>
import FormularioPessoa from './components/FormularioPessoa.vue';
import '../src/assets/estilos/AppVue.css';


export default {
  components: {
    FormularioPessoa
  }
}
</script>

