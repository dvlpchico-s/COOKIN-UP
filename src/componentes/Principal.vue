<script lang="ts">
import SelecionarIngredientes from './SelecionarIngredientes.vue';
import SuaLista from './SuaLista.vue';
import Tag from './Tag.vue'
export default {
    data(vm) {
        return{
            ingredientes:['Alho','Manteiga','Orégano']
        };
    },
    components: {SelecionarIngredientes, Tag,SuaLista}
}
</script>

<template>
    <main class="conteudo-principal">
        <section>
            <SuaLista :ingredientes="ingredientes" />
            
        </section>
        <SelecionarIngredientes />
    </main>
</template>

<style scoped>
.conteudo-principal {
    padding: 6.5rem 7.5rem;
    border-radius: 3.75rem 3.75rem 0rem 0rem;
    background: var(--creme, #FFFAF3);
    color: var(--cinza, #444);

    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 5rem;
}

</style>
