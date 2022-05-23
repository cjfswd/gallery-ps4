<script setup lang="ts">
import 'lazysizes';
import 'animate.css';

const router = useRouter();

router.beforeEach(() => {
  document.getElementById('main').scroll({ top: 0, behavior: 'smooth' })
})
</script>
<template>
  <Head>
    <Title>PS4 - Photo Project</Title>
  </Head>
  <header>
    <MoleculeNavbar />
  </header>
  <main id="main"
    style="overflow-y: scroll;overflow-x: hidden;padding-left:12px; padding-top: 12px; padding-bottom: 12px; height: calc(100vh - 64px);">
    <KeepAlive>
      <NuxtPage class="animate__animated animate__fadeInLeft" />
    </KeepAlive>
  </main>
</template>

<style>
:root {
  --animate-duration: 1000ms;
}

.lazyload,
.lazyloading {
  opacity: 0;
  transform: scale(0);
}

.lazyloaded {
  opacity: 1;
  transform: scale(1);
  transition: opacity 3000ms;
}

@font-face {
  font-family: "The-Rave-Is-In-Your-Pants";
  src: local("The-Rave-Is-In-Your-Pants"),
    url("assets/font/The-Rave-Is-In-Your-Pants.otf") format("opentype");
}

@font-face {
  font-family: "Zrnic";
  src: local("Zrnic"), url("assets/font/zrnic-rg.ttf") format("truetype");
}

#__nuxt {
  font-family: "The-Rave-Is-In-Your-Pants", "Zrnic";
  font-weight: 100;
  font-size: 14px;
  word-spacing: 10px;
  color: #003791;
}

main {
  font-size: 12px;
  font-family: "Ubuntu", sans-serif;
  word-spacing: 6px;
}

::-webkit-scrollbar {
  width: 12px;
}

::-webkit-scrollbar-track {
  background: transparent;
}

::-webkit-scrollbar-thumb {
  background: #003791;
  border-radius: 12px;
  border: 4px solid rgba(0, 0, 0, 0);
  background-clip: padding-box;
}
</style>
