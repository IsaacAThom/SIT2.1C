<template>
  <HelloWorld />
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}

body {
  /* Variables for use throughout */
  --bgColor1: #f5f5f5;
  --bgColor2: #eeeeee50;
  --bgColor2Hover: #fafafa50;
  --bgColor3: #ef9c9c;
  --bgColor3Hover: #e76d6d;
  --bgColor4: #a3ffa3;
  --bgColor4Hover: #73e373;
  --textPrimary: #000000;
  --boxShadow1: 3px 3px 6px 2px #9e9e9e50;
  --boxShadow2: 3px 3px 6px 2px #61616175;
  --bgGradient: linear-gradient(0deg, rgba(224,224,224,1) 0%, rgba(250,250,250,0) 100%);

  background: var(--bgColor1);
  min-width: 500px;
  transition: 0.25s;
}
/* Swapping variables values for dark mode */
.dark-mode {
  --bgColor1: #212121;
  --bgColor2: #61616150;
  --bgColor2Hover: #75757550;
  --bgColor3: #6c383850;
  --bgColor3Hover: #ac404050;
  --bgColor4: #2b422950;
  --bgColor4Hover: #3d793750;
  --textPrimary: #fafafa;
  --boxShadow1: 3px 3px 6px 2px #0b0b0b50;
  --boxShadow2: 3px 3px 6px 2px #00000075;
  --bgGradient: linear-gradient(0deg, rgba(66,66,66,1) 0%, rgba(33,33,33,0) 100%);
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: var(--textPrimary);
  margin-top: 60px;
  border: 2px solid var(--textPrimary);
  border-radius: 20px;
  padding: 10px 0px;
  background: var(--bgGradient);
  box-shadow: var(--boxShadow1);
}
</style>
