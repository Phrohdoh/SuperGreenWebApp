<template>
  <BoxSection
    icon='section-blower.svg'
    title='Blower control'
    color='#7DB0BB'
    :expanded='expanded'>
    <div :id='$style.body'>
      <BlowerControlSubSection schedule='on' param='blower_day' :expanded="expanded" />
      <BlowerControlSubSection schedule='off' param='blower_night' :expanded="expanded" />
    </div>
    <BoxSectionExpander @click='toggleExpand' :expanded='expanded' ref='expander' />
  </BoxSection>
</template>

<script>

import BoxSection from '~/components/boxsection'
import BlowerControlSubSection from '~/components/blowercontrolsubsection'
import BoxSectionExpander from '~/components/boxsectionexpander'

export default {
  components: { BoxSection, BlowerControlSubSection, BoxSectionExpander, },
  data() {
    return {
      expanded: false,
    }
  },
  computed: {
    controller() {
      return this.$store.getters['controllers/getSelected']
    },
  },
  methods: {
    toggleExpand() {
      this.$data.expanded = !this.$data.expanded
    }
  },
}

</script>

<style module lang=stylus>

#body
  display: flex
  flex: 1
  width: 100%
  @media screen and (max-width: 600px)
    flex-direction: column

</style>
