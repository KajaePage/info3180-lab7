<template>
   <div class="upload-container">
       <h1>Upload Form</h1>
       <br>
       <UploadForm/>
   </div>
</template>
<script>
import UploadForm from '@/components/UploadForm.vue'

export default {
    data() {
        return{};
    },
    components: { UploadForm }
}
</script>
<style>
.upload-container {
  margin: auto;
  margin-top: 20px;
  width: 50%;
  height: 488px;
  padding: 10px;
}
</style>