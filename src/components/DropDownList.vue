<template>
	<div
		class="drop-down-list"
		v-click-outside="collapse"
	>
		<div @click="toggle" class="select">
			<span class="label">{{value}}</span>
			<span
				:style="selectIconStyle"
				class="icon icon-select"
			></span>
		</div>
		<transition name="fade">	
			<div
				v-if="!isCollapsed"
				class="options"
			>
				<div
					class="option-item"
					v-for="option in options"
					:key="option"
					@click="onChange(option), collapse()"
				>{{option}}</div>
			</div>
		</transition>
	</div>
</template>

<script>
import ClickOutside from 'vue-click-outside'

export default {
	name: 'drop-down-list',
	props: {
		options: {
			type: Array,
			default: () => [ 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12 ]
		},
		value: {
			type: [ String, Number ]
		}
	},
	data () {
		return {
			isCollapsed: true
		}
	},
	computed: {
		selectIconStyle () {
			return this.isCollapsed ? {} : { transform: 'rotate(180deg)' }
		}
	},
	methods: {
		onChange (value) {
			this.$emit('input', value)
		},
		collapse () {
			this.isCollapsed = true
		},
		toggle () {
			this.isCollapsed = !this.isCollapsed
		}
	},
	directives: {
		ClickOutside
	}
}
</script>

<style lang="css" scoped>
.drop-down-list {
	position: relative;
	line-height: 40px;
	height: 40px;
	width: 300px;
	border: solid 1px #ddd;
	border-radius: 4px;
	text-align: left;
	text-indent: 20px;
}
.select {
	height: 40px;
}
.icon-select {
	transition: transform .2s ease;
	position: absolute;
	top: 15px;
	right: 10px;
	width: 0; 
  height: 0; 
  border-left: 10px solid transparent;
  border-right: 10px solid transparent;
  border-top: 10px solid #ddd;
}
.options {
	position: absolute;
	top: 42px;
	width: 100%;
	border: solid 1px #ddd;
	border-radius: 4px;
	max-height: 200px;
	overflow-y: auto;
}
.option-item {
	cursor: pointer;
}
.option-item:hover {
	background-color: #eee;
}
.fade-enter-active, .fade-leave-active {
	transition: opacity .2s ease, transform .2s cubic-bezier(0.175, 0.885, 0.32, 1.275);
	transform-origin: top;
}
.fade-enter, .fade-leave-to {
	opacity: 0;
	transform: scaleY(.5);
}
</style>
