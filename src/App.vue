<template lang="pug">
.wrapper
  wysiwyg#editor(v-model="msg")
  hr
  h3 Label preview
  .preview(v-html="preview")   
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      msg: `
        
      <table>
        <tbody>
        <tr>
          <td>

            <ol>
              <li>Item #1</li>
              <li>Item #2</li>
            </ol>
          </td>
          <td>
            <ul>
              <li>Item #1</li>
              <li>Item #2</li>
            </ul>
          </td>
        </tr>
        </tbody>
        </table>
      
      `
    }
  },
  computed:{
    preview(){
      return this.msg;
    }
  }
}
</script>

<style>
* {
  margin:0;
  padding: 0;
  box-sizing: border-box;
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

body {
  font-family: -apple-system,
                BlinkMacSystemFont,
                "Segoe UI",
                Roboto,
                Oxygen-Sans,
                Ubuntu,
                Cantarell,
                "Helvetica Neue",
                sans-serif;
}

.preview{
    border: 1px solid black;
    border-radius: 5px;
    width: 6in;
    height: 4in;
    overflow: hidden;
}          

@media print {
  #editor, hr, h3{
    display: none;
  }

  .preview {
    border: none;
    position: absolute;
    top: 0;
  }  

  @page {
    size: auto;   /* auto is the initial value */
      margin: 0;  /* this affects the margin in the printer settings */
  }
}
</style>
