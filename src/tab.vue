<template lang="pug">
.bunt-tab(:id="id", role="tabpanel", :tabindex="active ? '0' : null", :aria-hidden="!active ? 'true' : null", v-show="active")
	slot
</template>
<script>
export default {
	name: `bunt-tab`,
	props: {
		header: String,
		icon: String,
		disabled: {
			type: Boolean,
			default: false
		},
		id: String,
	},
	computed: {
		active () {
			return this.$parent.activeTabObj === this
		}
	},
	watch: {
		active (val) {
			if (val) {
				this.$emit('selected', this.id)
			} else {
				this.$emit('deselected', this.id)
			}
		}
	},
	created () {
		this._isTab = true
	}
}
</script>
