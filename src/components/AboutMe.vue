<script setup>
const resumeUrl = new URL('../assets/Resume.pdf', import.meta.url).href
const codeImg = new URL('../assets/code.png', import.meta.url).href
</script>

<template>
  <section class="about">
    <h1>Ульянов Роман</h1>
    <p>Фронтенд‑разработчик. Делаю быстрые и удобные веб‑сайты, Linux администратор, а также младший специалист по виртуализации.</p>
    <div class="center">
      <a :href="resumeUrl" target="_blank" rel="noopener" class="btn">
        <img class="btn-icon" :src="codeImg" alt="" aria-hidden="true" />
        Открыть резюме (PDF)
      </a>
    </div>
  </section>
  
</template>

