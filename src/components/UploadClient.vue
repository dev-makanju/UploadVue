<template>
   <div class="img_wrapper">
      <button @click="openWidget">Upload</button>
   </div>
</template>

<script>

export default {
   name: 'UploadClient',
   components: {
   },
   data(){
      return {
      }
   },
   methods: {
      openWidget(){
         const widget = window.cloudinary.createUploadWidget(
            { 
               cloud_name: 'dyz1ogpac',
               upload_preset: 'upload-demo',
            },//fonfig
            (error, result) => {
               if(!error && result && result.event == "success"){
                  console.log('Huray!, Image Uploaded...' , result.info);
                  window.open(result.info.url,"_target")
                  widget.close();
               }
            }//callback
         )
         widget.open();
      }
   }

}

</script>

<style lang="css" scoped>
   .img_wrapper button{ 
      padding: 7px 20px;
      font-size: 20px;
      border: none;
      border-radius: 5px;
      cursor: pointer;  
   } 
</style>