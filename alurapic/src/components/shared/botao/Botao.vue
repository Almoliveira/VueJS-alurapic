<template>
  <button  class="botao" :class="estiloDoBotao" :type="tipo" @click="disparaAcao()">
    {{ rotulo }}
  </button>
</template>


<script>
export default {
  props: {
       tipo: {
           type: String, 
           required: true
       },

       rotulo: {
           type: String, 
           required: true
       },

       confirmacao: Boolean,
       
       estilo: String
   },

    computed: {
        estiloDoBotao(){
            if(this.estilo == "padrao" || !this.estilo)
                return "botao botao-padrao";
            if(this.estilo == "perigo")
                return "botao botao-perigo";
            
        }
    },

  methods: {
    disparaAcao() {
      if (this.confirmacao) {
        if (confirm("Confirma operação?")) {
          this.$emit("botaoAtivado");
        }
        return;
      }
      this.$emit("botaoAtivado");
    },
  },
};
</script>


<style scoped lang="scss">

@import './Botao.scss';
</style>