<script setup lang="js">
    var search = document.getElementById('search');
    var log = document.getElementById('log');
    
    /* keyup 
   */
search.addEventListener('keyup', function() {
  // Cria um <li> e adiciona na <ul> apenas para exemplificar
  var li = document.createElement('li');
  li.innerHTML = "Pesquisando: " + this.value;
  log.insertBefore(li, log.firstChild);
});
</script>

<template>
    <input id="search">
    <hr>
<ul id="log"></ul>
</template>