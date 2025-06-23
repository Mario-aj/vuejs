<script lang="ts">
import { obterCategorias } from "@/http/index";
import type { ICategoria } from "@/interfaces/ICategoria";

export default {
  data() {
    return {
      categorias: [] as ICategoria[],
    };
  },
  async created() {
    this.categorias = await obterCategorias();
  },
};
</script>

<template>
  <section class="selecionar-ingredientes">
    <h class="cabecalho titutlo-ingredientes">Ingredientes</h>

    <p class="paragrafo-lg intrucoes">
      Selecione abaixo os ingredientes que voçê quer usar nesta receita:
    </p>

    <ul class="categorias"></ul>

    <p class="paragrafo dica">
      *Atenção: consideramos que voçê tem em casa sal, pimento e água.
    </p>
  </section>
</template>

<style scoped>
.selecionar-ingredientes {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.titulo-ingredientes {
  color: var(--verde-medio, #3d6d4a);
  display: block;
  margin-bottom: 1.5rem;
}

.instrucoes {
  margin-bottom: 2rem;
}

.categorias {
  margin-bottom: 1rem;
  display: flex;
  justify-content: center;
  gap: 1.5rem;
  flex-wrap: wrap;
}

.dica {
  align-self: flex-start;
  margin-bottom: 3.5rem;
}

@media only screen and (max-width: 767px) {
  .dica {
    margin-bottom: 2.5rem;
  }
}
</style>
