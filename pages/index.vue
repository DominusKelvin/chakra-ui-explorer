<template>
  <c-box
    as="main"
    d="flex"
    align-items="space-between"
    flex-direction="column"
    w="auto"
    p="16"
  >
    <c-input v-model="search" placeholder="Search components..." size="lg" mb="10" is-full-width />
    <c-grid template-columns="repeat(4, 1fr)" gap="3" p="5">
      <c-box v-for="(chakraComponent, index) of filteredComponents" :key="index" h="10">
        {{ chakraComponent.name }}
        <c-badge>
          <c-link
            is-external
            :href="lowercase(`https://vue.chakra-ui.com/${chakraComponent.name}`)"
          >
            <c-icon name="info" size="18px" />
          </c-link>
        </c-badge>
      </c-box>
    </c-grid>
  </c-box>
</template>

<script>
import { CBox, CInput, CGrid, CLink, CBadge, CIcon } from '@chakra-ui/vue'
import { components as chakraComponents } from '../data'
export default {
  components: {
    CBox,
    CInput,
    CGrid,
    CBadge,
    CIcon,
    CLink
  },
  data () {
    return {
      search: ''
    }
  },
  computed: {
    filteredComponents () {
      return chakraComponents.filter((component) => {
        return this.lowercase(component.name).includes(this.lowercase(this.search))
      })
    }
  },
  methods: {
    lowercase (value) {
      return value.toLowerCase()
    }
  }
}
</script>
