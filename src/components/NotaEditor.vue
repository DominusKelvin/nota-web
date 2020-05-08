<template>
  <div class="editor">
    <editor-content class="editor__content" :editor="editor" />
  </div>
</template>

<script>
import { Editor, EditorContent } from "tiptap";
import {
  Blockquote,
  CodeBlock,
  HardBreak,
  Heading,
  OrderedList,
  BulletList,
  ListItem,
  TodoItem,
  TodoList,
  Bold,
  Code,
  Italic,
  Link,
  History,
  Placeholder,
} from "tiptap-extensions";

import Title from "./tipTapSchemas/Title";
import Doc from "./tipTapSchemas/Doc";

export default {
  name: "NotaEditor",
  props: {},
  computed: {},
  data() {
    return {
      editor: new Editor({
        autofocus: true,
        extensions: [
          new Doc(),
          new Title(),
          new Blockquote(),
          new BulletList(),
          new CodeBlock(),
          new HardBreak(),
          new Heading(),
          new ListItem(),
          new OrderedList(),
          new TodoItem(),
          new TodoList(),
          new Bold(),
          new Code(),
          new Italic(),
          new Link(),
          new History(),
          new Placeholder({
            showOnlyCurrent: false,
            emptyNodeText: (node) => {
              if (node.type.name === "title") {
                return "Note Title";
              }
              return "start taking notes...";
            },
          }),
        ],
      }),
    };
  },
  components: {
    EditorContent,
  },
  beforeDestroy() {
    this.editor.destroy();
  },
};
</script>
<style lang="scss">
@import "../assets/scss/main.scss";
.editor *.is-empty:nth-child(1)::before,
.editor *.is-empty:nth-child(2)::before {
  content: attr(data-empty-text);
  float: left;
  color: #aaa;
  pointer-events: none;
  height: 0;
}
</style>
