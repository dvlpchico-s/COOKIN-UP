<script lang="ts">
import Rodape from "./Rodape.vue"
import MostrarReceitas from "./MostrarReceitas.vue";
import SelecionarIngredientes from "./SelecionarIngredientes.vue";
import SuaLista from "./SuaLista.vue";
import Tag from "./Tag.vue";
import BotaoPrincipal from "./BotaoPrincipal.vue";

 
type Pagina = 'SelecionarIngredientes' | 'MostrarReceitas';
export default {
  data(vm) {
    return {
      ingredientes: [] as string[],
      conteudo: 'SelecionarIngredientes' as Pagina
    };
  },
  components: { SelecionarIngredientes, Tag, SuaLista , Rodape ,MostrarReceitas,BotaoPrincipal},
  methods: {
    adicionarIngredientes(ingredientes: string) {
      this.ingredientes.push(ingredientes);
    },
    removerIngrediente(ingrediente: string) {
      this.ingredientes = this.ingredientes.filter(
        (iLista) => ingrediente !== iLista
      );
    },
    navegar(pagina:Pagina){
      this.conteudo = pagina;
    }
  },
};
</script>

<template>
  <main class="conteudo-principal">
    <section>
      <SuaLista :ingredientes="ingredientes" />
    </section>
    <SelecionarIngredientes v-if="conteudo === 'SelecionarIngredientes'"
      @adicionar-ingrediente="adicionarIngredientes"
      @remover-ingrediente="removerIngrediente" 
      @buscar-receitas="navegar('MostrarReceitas')"
    />
    <MostrarReceitas
    v-else-if="conteudo == 'MostrarReceitas'"/>
    <Rodape/>
  </main>
</template>

<style scoped>
.conteudo-principal {
  padding: 6.5rem 7.5rem;
  border-radius: 3.75rem 3.75rem 0rem 0rem;
  background: var(--creme, #fffaf3);
  color: var(--cinza, #444);

  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 5rem;
}
</style>
