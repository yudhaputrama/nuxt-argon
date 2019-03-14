<template>
  <div>
    <starter-header/>
    <nuxt />
    <starter-footer/>
  </div>
</template>

<script>
import StarterHeader from '@/components/starter/StarterHeader'
import StarterFooter from '@/components/starter/StarterFooter'

export default {
  components: {
    StarterHeader,
    StarterFooter
  }
}
</script>
