<script setup>

</script>

<template>
  <section class="grid gap-4 mx-2 my-4 grid-cols-2 main-wrapper">
    <div class="bg-zinc-900 pl-2 pt-2 text-white text-xl rounded">
      BentriList é uma aplicação de listagem de filmes, séries, animes, mangas ou livros! <br>
      É real, você pode listar qualquer coisa!
      <div class="text-center">
        <ul class="feature-list">
          <li>- Listas dinâmicas</li>
          <li>- Salve sua lista no próprio navegador!</li>
          <li>- Exporte a lista como JSON</li>
          <li>- Incremente a sua lista o quanto quiser e quando quiser!</li>
        </ul>
      </div>
    </div>
    <div class="bg-zinc-900 pt-2 text-white text-center text-xl rounded">
      BetriList é um aplicativo web desenvolvido, da Bentricode! <br>
      <a href="/about" target="_blank" class="saibamais">Saiba Mais</a>
    </div>
  </section>
  <section class="grid mx-2 my-2 gap-1 grid-cols-2 p-4 rounded list-example">
    <article class="mx-auto">
      <img src="bentrilistex.JPG" class="rounded exemplolista" alt="">
    </article>
    <article class="my-auto list-example-text">
      <p class="text-left mb-2">É assim que uma lista Bentrilist se parece! <br> Deseja criar a sua ? <br></p>
      <a href="/list" class="border border-yellow rounded p-1 mt-1 ml-4 text-right to-list">Sim, mal posso esperar!</a>
    </article>
  </section>
  <section class="grid gap-4 mx-2 my-4 grid-cols-2 main-wrapper">
    <div class="bg-zinc-900 pl-2 pt-2 text-white text-xl rounded">
      <img class="mx-auto somegif" src="https://media.tenor.com/QLh0PhunTj8AAAAC/anime-typing.gif" />
      <p class="mx-auto text-center">Construa sua lista pessoal e gratuita!</p>
    </div>
    <div class="bg-zinc-900 pt-2 text-white text-center text-xl rounded">
      <div class="text-center">
        Este projeto funciona graças à
        <div class="flex justify-evenly mt-2 wrap">
          <img src="./../assets/logo.svg" width="140px"/>
        </div>
      <a href="/about" target="_blank" class="saibamais">Saiba Mais</a>
      </div>
    </div>
  </section>
</template>

<style scoped>
.feature-list{
  font-size: 12pt;
}
.list-example{
  background-color: #4B1F99;
  color: #faf02f;
}
.list-example-text{
  font-size: 20pt;
}
.exemplolista{
  max-width: 740px;
  width:100%;
}
.to-list{
  background-color:#451c8b;
  font-size: 23pt;
  font-weight: bold;
}
.to-list:hover{
  background-color:#5422aa;
}
.saibamais{
  color: #6a2ada;
}
.saibamais:hover{
  color: #faf02f;
}
.somegif{
  max-width: 500px;
  width: 100%;
}
</style>
