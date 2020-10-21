<template>
  <div>
    <prism-editor
      class="my-editor"
      v-model="code"
      :highlight="highlighter"
      line-numbers
    ></prism-editor>
  </div>
</template>

<script>
// import Prism Editor
import { PrismEditor } from "vue-prism-editor";
import "vue-prism-editor/dist/prismeditor.min.css"; // import the styles somewhere

// import highlighting library (you can use any library you want just return html string)
import { highlight, languages } from "prismjs/components/prism-core";
import "prismjs/components/prism-clike";
import "prismjs/components/prism-javascript";
import "prismjs/themes/prism-tomorrow.css"; // import syntax highlighting styles

import { defineComponent, onMounted, ref } from "vue";
export default defineComponent({
  components: {
    PrismEditor,
  },
  setup() {
    onMounted(() => {
      console.log("OKKK");
    });
    const code = ref('console.log("Hello World")');
    const highlighter = (code) => {
      return highlight(code.value, languages.js); // languages.<insert language> to return html with markup
    };
    return { code, highlighter };
  },
});
</script>
