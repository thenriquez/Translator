<template>
  <div id="app" class="text-center">
<h1>Word Translator</h1>
<h5>Powered with Vue</h5>
<TranslateForm v-on:formSubmit ="translateText"></TranslateForm>
<TranslateOutput v-text="translatedText"></TranslateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'
export default {
  name: 'app',
  components:{
    TranslateForm,
    TranslateOutput
  },
  data: function(){
    return {
      translatedText:''
    }
  },
  methods:{
    translateText:function(text, language){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180830T204122Z.16e56ec0dc0af8df.ab50fd8f7a89c4af0db64aa32b6507a43c11b664&lang='+language+'&text='+text)
      .then((response) => {
        this.translatedText = response.body.text[0];
      
    
      });
  }
  }
}
</script>

<style>



</style>
