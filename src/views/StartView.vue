<script setup lang="ts">
</script>

<template>
  <main>
    <div>
      <div style="margin-top: 20rem;margin-bottom: 8rem;">
        <Clock></Clock>
      </div>
      <div class="links">
        <a href="https://calendar.google.com/calendar/">Calendar</a>
        <a href="https://github.com">Github</a>
        <a href="https://gmail.com">Gmail</a>
        <a href="https://notion.so">Notion</a>
      </div>
      <div id="comment">
        <p class="comment"> // Everything not saved will be lost... </p>
      </div>
      <div id="terminal-line" class="terminal">
        <h1 class="host">guilherme@moog:~$</h1>
        <input class="search" type="text" v-model="terminal" name="" id="" @keyup.enter="search" autofocus>
      </div>

    </div>
  </main>
</template>


<script>
  import { onMounted, ref, toRaw } from 'vue';
  import Clock from '../components/Clock.vue'

  const search = () => {
    if(!terminal.value) return

    let query = toRaw(terminal.value)
    
    //get firs word
    let provider = query.split(' ')[0]
    console.log(query)
    
    provider == 'wiki'? window.location.href = `https://en.wikipedia.org/w/index.php?search=${query.slice(4)}`: window.location.href = `http://www.google.com/search?q=${query}`

    //window.location.href = `http://www.google.com/search?q=${query}`
    //window.location.href = `https://en.wikipedia.org/w/index.php?search=${query}`
      
    
  }
  const terminal = ref()
  

  export default {
    components: {
      Clock
    },
    data() {
      return {
        terminal,
        search
      };
    },
    watch: {
      banco(newValue) {
      }
    },
      
  }
</script>

<style>

  

</style>
