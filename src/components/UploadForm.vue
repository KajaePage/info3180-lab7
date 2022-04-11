
<script>
export default ({
    created() {
 this.getCsrfToken();
},
    data() {
        return{
            csrf_token: ''
        }
    },
    methods:{
        uploadPhoto(){
            let uploadForm = document.getElementById('uploadForm');
            let form_data = new FormData(uploadForm);
            fetch("/api/upload", {
                method: 'POST',
                body: form_data,
                headers: {
                        'X-CSRFToken': this.csrf_token
                }
                })
                .then(function (response) {
                return response.json();
                })
                .then(function (data) {
                // display a success message
                console.log(data);
                })
                .catch(function (error) {
                console.log(error);
                });
        },
        getCsrfToken() {
        let self = this;
        fetch('/api/csrf-token')
        .then((response) => response.json())
        .then((data) => {
        console.log(data);
        self.csrf_token = data.csrf_token;
        })
        }
    }
})
</script>
<template>
    <form id="uploadForm" method='POST' @submit.prevent="uploadPhoto">
          <input type="hidden" name="csrf_token" value="csrf"/>
          <label class = "form-control-label"> Description </label>
          <textarea name="description" rows="3" cols = "10" class = "form-control"></textarea>
          <br>
          <label class="l">Photo Upload</label>
          <input type="file" name="image" class="below" accept="image/*" draggable="true">
          <button type="submit" name="submit" class="btn btn-primary">Submit</button>
    </form>
</template>
<style>
.form-control-label{
    padding-bottom: 10px;
}
.input{
    width: 100%;
}
.below{
    position: absolute;
    top: 380px;
    left: 400px;
}
.btn{
    position:absolute;
    top: 450px;
    left: 400px;
}
</style>