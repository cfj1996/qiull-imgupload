<template>
  <div id="app">
    <div ref="editor" style="height: 500px"></div>
  </div>
</template>

<script>
  import 'quill/dist/quill.core.css'
  import 'quill/dist/quill.snow.css'
  import 'quill/dist/quill.bubble.css'
  import $Quill from './plugins/quill'
  const Quill = window.Quill || $Quill
export default {
  name: 'app',
  data(){
    return {
      content: '',
      options: {
        upload: '/api/igloo',
        theme: 'snow',
        modules: {
          toolbar: [
            ['bold', 'italic', 'underline', 'strike'],
            ['blockquote', 'code-block'],
            [{ 'header': 1 }, { 'header': 2 }],
            [{ 'list': 'ordered' }, { 'list': 'bullet' }],
            [{ 'script': 'sub' }, { 'script': 'super' }],
            [{ 'indent': '-1' }, { 'indent': '+1' }],
            [{ 'direction': 'rtl' }],
            [{ 'size': ['small', false, 'large', 'huge'] }],
            [{ 'header': [1, 2, 3, 4, 5, 6, false] }],
            [{ 'color': [] }, { 'background': [] }],
            [{ 'font': [] }],
            [{ 'align': [] }],
            ['clean'],
            ['link', 'image', 'video']
          ]
        },
      }
    }
  },
  mounted() {
    this.quill = new Quill(this.$refs.editor, this.options)
    this.quill.on('text-change', () => {
      let html = this.$refs.editor.children[0].innerHTML
      if (html === '<p><br></p>') html = ''
      this.content = html
    })
  },
  beforeDestroy() {
    this.content = ''
    this.quill = null
    delete this.quill
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
