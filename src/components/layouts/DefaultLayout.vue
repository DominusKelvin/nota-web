<template>
  <c-theme-provider>
    <c-color-mode-provider v-slot="{ colorMode }">
      <c-box
        font-family="body"
        :bg="colorMode === 'light' ? 'white' : 'gray.800'"
        :color="colorMode === 'light' ? 'black' : 'whiteAlpha.900'"
      >
        <c-reset />
        <c-flex max-h="100vh">
          <side-bar />
          <c-box
            :class="styles(colorMode)"
            as="section"
            w="100%"
            height="100vh"
            overflow-y="auto"
            pt="20"
            :px="[10, 10, 20, '14rem']"
          >
            <slot></slot>
          </c-box>
        </c-flex>
      </c-box>
    </c-color-mode-provider>
  </c-theme-provider>
</template>

<script>
import {
  CThemeProvider,
  CReset,
  CColorModeProvider,
  CBox,
  CFlex,
  Css,
} from "@chakra-ui/vue";
import { css } from "emotion";
import SideBar from "@/components/SideBar.vue";
export default {
  name: "DefaultLayout",
  components: {
    CThemeProvider,
    CReset,
    CColorModeProvider,
    CBox,
    CFlex,
    SideBar,
  },
  data() {
    return {
      thBg: {
        light: "gray.50",
        dark: "whiteAlpha.100",
      },
      callout: {
        light: {
          bg: "rgb(254, 235, 200)",
          color: "black",
          borderLeft: "4px solid rgb(221, 107, 32)",
        },
        dark: {
          bg: "rgba(251, 211, 141, 0.16)",
          color: "inherit",
          borderLeft: "4px solid rgb(251, 211, 141);",
        },
      },
      code: {
        light: {
          bg: "#fefcbf",
          color: "#744210",
        },
        dark: {
          bg: "rgba(250, 240, 137, 0.16)",
          color: "rgb(250, 240, 137)",
        },
      },
    };
  },
  computed: {
    styles() {
      return (colorMode) =>
        css(
          Css({
            th: {
              bg: this.thBg[colorMode],
            },
            ".preview-panel": {
              borderColor: this.thBg[colorMode],
            },
            "table, p": {
              code: {
                ...this.code[colorMode],
                fontSize: "sm",
              },
            },
            "h1, h2, h3": {
              code: this.code[colorMode],
            },
            li: {
              code: {
                ...this.code[colorMode],
                fontSize: "sm",
              },
            },
          })(this.$chakra.theme)
        );
    },
  },
};
</script>
