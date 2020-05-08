<template>
  <c-box
    as="nav"
    p="4"
    :display="['none', null, 'block']"
    max-width="18rem"
    width="full"
    border-right="1px"
    border-color="gray.200"
    h="100vh"
    overflow-y="auto"
  >
    <side-nav-content />
    <c-box as="div">
      <c-button
        @click="$toggleColorMode"
        variant="ghost"
        variantColor="gray"
        :aria-label="
          colorMode === 'light' ? 'Switch to dark mode' : 'Switch to light mode'
        "
        :left-icon="colorMode === 'light' ? 'moon' : 'sun'"
      >
        {{ colorMode }}
      </c-button>
    </c-box>
  </c-box>
</template>

<script>
import { CBox, CButton } from "@chakra-ui/vue";
import SideNavContent from "@/components/SideNavContent.vue";
export default {
  name: "SideBar",
  inject: ["$chakraColorMode", "$toggleColorMode"],
  components: {
    CBox,
    SideNavContent,
    CButton,
  },
  computed: {
    colorMode() {
      return this.$chakraColorMode();
    },
  },
};
</script>

<style lang="scss" scoped></style>
