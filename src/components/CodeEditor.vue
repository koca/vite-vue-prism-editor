<template>
  <div>
    <prism-editor class="my-editor" v-model="editorCode" :highlight="highlighter" line-numbers></prism-editor>
  </div>
</template>

<script>
// import Prism Editor
import { PrismEditor } from 'vue-prism-editor'; //
import 'vue-prism-editor/dist/prismeditor.min.css'; // import the styles somewhere

// import highlighting library (you can use any library you want just return html string)
import prism from 'prismjs';
import 'prismjs/themes/prism-tomorrow.css'; // import syntax highlighting styles

import { defineComponent, onMounted, ref } from 'vue';
export default defineComponent({
  components: {
    PrismEditor,
  },
  setup() {
    const editorCode = ref('console.log("Hello World")');
    const highlighter = (code) => {
      return prism.highlight(code, prism.languages.js);
    };
    return { editorCode, highlighter };
  },
});
</script>

<style>
.my-editor {
  /* we dont use `language-` classes anymore so thats why we need to add background and text color manually */
  background: #2d2d2d;
  color: #ccc;

  /* you must provide font-family font-size line-height. Example: */
  font-family: Fira code, Fira Mono, Consolas, Menlo, Courier, monospace;
  font-size: 14px;
  line-height: 1.5;
  padding: 5px;
}

/* optional class for removing the outline */
.prism-editor__textarea:focus {
  outline: none;
}
</style>
