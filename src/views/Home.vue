<template>
	<v-container>
		<div class="text-center">Morita room temperature</div>
		<chartcontain/>
	</v-container>
</template>

<script>
// @ is an alias to /src
import chartcontain from './chartcontain.vue'
export default {
  name: 'Home',
  components: {
	chartcontain
  }
}
</script>
