<template>
  <div>
    <CodeEditor />
  </div>
</template>

<script>
import { defineComponent, onMounted } from "vue";
import CodeEditor from "./components/CodeEditor.vue";

export default defineComponent({
  name: "App",
  components: {
    CodeEditor,
  },
  setup() {
    onMounted(() => {
      console.log("hey");
    });
  },
});
</script>
