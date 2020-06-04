<template>
  <div class="container">
    <c-theme-provider>
      <c-color-mode-provider #default="{ colorMode }">
        <c-box
          v-bind="mainStyles[colorMode]"
          w="100vw"
          h="100vh"
          as="section"
        >
          <c-reset />
          <nav-bar />
          <nuxt />
        </c-box>
      </c-color-mode-provider>
    </c-theme-provider>
  </div>
</template>

<script>
import { CThemeProvider, CColorModeProvider, CReset, CBox } from '@chakra-ui/vue'
import NavBar from '@/components/NavBar'
export default {
  name: 'DefaultLayout',
  components: {
    CThemeProvider,
    CColorModeProvider,
    CReset,
    CBox,
    NavBar
  },
  data () {
    return {
      mainStyles: {
        dark: {
          bg: 'gray.900',
          color: 'whiteAlpha.900'
        },
        light: {
          bg: 'whiteAlpha.900',
          color: 'gray.900'
        }
      }
    }
  }
}
</script>
