<template>
  <section class="mx-2 my-4 bg-fuchsia-700 pl-2 rounded main-wrapper">
    <article>
      BentriList é uma aplicação de listagem de filmes, séries, animes, mangas ou livros. Desenvolvida como um projeto Vue JS. <br>
      É real, você pode listar qualquer coisa!
      <div class="text-center">
        <ul class="feature-list">
          <li>- Listas dinâmicas</li>
          <li>- Salve sua lista no próprio navegador!</li>
          <li>- Exporte a lista como JSON</li>
          <li>- Incremente a sua lista o quanto quiser e quando quiser!</li>
        </ul>
      </div>
      <p>A BentriList foi desenvolvida como um projeto prático de Vue JS 3.</p>
    </article>
  </section>
</template>

<style>
.main-wrapper{
  color: #E6DE45;
}
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
