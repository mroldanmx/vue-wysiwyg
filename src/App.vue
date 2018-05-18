<template lang="pug">
.wrapper
  TemplateList
  
  wysiwyg#editor(v-model="msg")
  
  .half-width
    h3 Label preview
    .preview(v-html="preview" :style="style")   
    .label-options.no-print
      h3 Label options
      label width 
      input(type="text" placeholder="Label width" v-model="lWidth")
      label height 
      input(type="text" placeholder="Label height" v-model="lHeight")
      select(v-model="selectedOrientation")
        option(v-for="(o, index) of labelOrientations" :value="o" :key="index") {{o}}
</template>

<script>
import TemplateList from './TemplateList';

export default {
  name: 'app',
  data () {
    return {
      labelUOM: 'in' ,
      lWidth: '6',
      lHeight: '4',
      labelOrientations: ['landscape', 'portrait'],
      selectedOrientation: 'landscape',
      msg: '',
    }
  },
  computed:{    
    preview(){
      return this.msg;
    },

    labelWidth(){
      return `${this.lWidth}${this.labelUOM}`;
    },

    labelHeight(){
      return `${this.lHeight}${this.labelUOM}`;
    },

    orientation(){
      if (this.selectedOrientation === 'landscape' ){
        return {}
      }      

      return { transform: 'rotate(90deg)' }
    },

    style(){
      return { width: this.labelWidth, height: this.labelHeight, ...this.orientation }
    },
  },

  methods:{
    getParamFromURL(paramName){
      let uri = window.location.search.substring(1); 
      let params = new URLSearchParams(uri);
      return params.get(paramName);
    }
  },
  mounted(){
    this.labelUOM = this.getParamFromURL('labelUOM') || this.labelUOM;
    this.lWidth = this.getParamFromURL('lWidth') || this.lWidth;
    this.lHeight = this.getParamFromURL('lHeight') || this.lHeight;
    this.selectedOrientation = this.getParamFromURL('selectedOrientation') || this.selectedOrientation;
  },

  components:{
    TemplateList
  }
}
</script>

<style>
* {
  margin:0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Arial Narrow';
}

@font-face{
  font-family: 'Arial Narrow';
  src: url('http://allfont.net/allfont.css?fonts=arial-narrow');
}

.wrapper {
  max-width: 800px;
  margin: 10em auto;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.half-width{
  width:50%; float: left;
}

.preview{
    border: 1px solid black;
    border-radius: 5px;
    overflow: hidden;
}          

.preview .barcode{
    overflow:hidden !important;
}


@media print {
  #editor, hr, h3, .no-print{
    display: none;
  }

  .preview {
    border: none;
    position: absolute;
    top: 0;
  }  

  .barcode{
    overflow:hidden !important;
  }
  

  @page {
    size: auto;   /* auto is the initial value */
      margin: 0;  /* this affects the margin in the printer settings */
  }
}

    .barcode{
        resize: both;                            
        overflow: auto;
    }

    .barcode img{  
        width: 100%;
    }
</style>
