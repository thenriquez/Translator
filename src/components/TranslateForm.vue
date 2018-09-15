<template>
  <div class="row" id="TranslateForm">
    <div class="col-md-7 col-md-offset-3">
<form v-on:submit="formSubmit" >
<!-- <input type="text" v-model="textToTranslate" placeholder="Enter a Word"> -->
<textarea class="form-control" v-model="textToTranslate"></textarea>
<input type="submit" class="btn btn-dark" value="Translate">
<select v-model="language" class="custom-select">
<option value="ru">Russian</option>
<option value="es">Spanish</option>
<option value="ht">Haitian</option>
<option value="jv">Japanese</option>

</select>

</form>

</div>
  </div>
</template>

<script>


export default {
  name: 'translateForm',

data(){
    return {
     
     textToTranslate:'',
     language: ''
    }
},
created() {
  this.language = 'es';
},

methods: {

formSubmit(e){
    this.$emit('formSubmit', this.textToTranslate,this.language);
    
    e.preventDefault();
    
    }
}
}
</script>

<style>
 form {
   text-align: center;
 }
</style>
