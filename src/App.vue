<template>
  <div>
    <UploadClient/>
  </div>
</template>

<script>

import UploadClient from '@/components/UploadClient.vue';

export default {
  name: 'App',
  components: {
    UploadClient
  }
}
</script>

<style>

* {
  padding: 0;
  margin: 0;
}

body {
  background: #2c3e50 ;
  height: 100vh;
  width: 100%;   
  display: flex;
  justify-content: center;
  align-items: center; 
}

#app {
  margin: 0;
  padding: 0;
}
</style>
