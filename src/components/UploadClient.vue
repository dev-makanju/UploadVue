<template>
   <div class="img_wrapper">
      <label for="upload">Drag or Click to upload</label>
      <p>Image should not be more than 2mb</p>
      <input
         class="imageInp" 
         id="upload"
         type="file" 
         @change="onUpload"
         accept="image/*">
   </div>
</template>

<script>

import cloudinaryConfig from '../../cloudinary';

export default {
   name: 'UploadClient',
   data(){
      return {
        file: {},
      }
   },
   methods: {
      onUpload(e){
         if(e.target.files[0].type === "image/*" &&  e.target.files[0].size  <= 2097152  ) {
           this.addFile(e.target.files[0]);
         }
      },
      addFile(value){
         console.log('hello');
         const file = value;
         console.log(file);
         cloudinaryConfig.upload(file).then(res => {
            console.log('Image uploaded', res);
         }).catch(err => {
            console.log('an error occured:' + err);
         })
      }
   }

}

</script>


<style lang="css" scoped>
   .imageInp {
      display: none;
   }

   .img_wrapper {
      border: 1px dashed #ccc;
      padding: 50px;
      border-radius: 5px;
   }

   .img_wrapper label {
      cursor: pointer;
   }

   .img_wrapper p {
      font-size: 12px;
      font-weight: 300;
      color:  #e74e3c;
      font-style: italic;
   }

</style>