<script lang="ts">
import SelecionarIngredientes from "./SelecionarIngredientes.vue";
import SuaLista from "./SuaLista.vue";
import Tag from "./Tag.vue";
export default {
  data(vm) {
    return {
      ingredientes: [] as string[],
    };
  },
  components: { SelecionarIngredientes, Tag, SuaLista },
  methods: {
    adicionarIngredientes(ingredientes: string) {
      this.ingredientes.push(ingredientes);
    },
    removerIngrediente(ingrediente: string) {
      this.ingredientes = this.ingredientes.filter(
        (iLista) => ingrediente !== iLista
      );
    },
  },
};
</script>

<template>
  <main class="conteudo-principal">
    <section>
      <SuaLista :ingredientes="ingredientes" />
    </section>
    <SelecionarIngredientes
      @adicionar-ingrediente="adicionarIngredientes"
      @remover-ingrediente="removerIngrediente"
    />
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
