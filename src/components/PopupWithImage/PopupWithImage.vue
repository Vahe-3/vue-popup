<template>
	<van-popup v-model:show="isOpen" position="bottom" class="popupWithImg">
		<div class="content">
			<div class="header">
				<div class="image-wrapper">
					<slot v-if="!imageUrl" name="image"></slot>
					<img v-if="imageUrl" :src="imageUrl" />
				</div>
				<div class="close-button"" @click="handleClose">&times;</div>
			</div>
			<div class="body">
				<slot v-if="!title" name="title"></slot>
				<h1 v-if="title">{{ title }}</h1>
				<slot v-if="!subtitle" name="subtitle"></slot>
				<h2 v-if="subtitle"> {{ subtitle }}</h2>
				<slot v-if="!subtitle" name="description"></slot>
				<p v-if="subtitle">{{ description }}</p>
				<slot name="content"></slot>
			</div>
		</div>
	</van-popup>
</template>

<script>
import { Popup } from 'vant';
export default {
	name: 'PopupWithImage',
	components: { 'van-popup': Popup },

	props: {
		imageUrl: {
			type: String,
			required: true
		},
		title: {
			type: String,
		},
		subtitle: {
			type: String,
		},
		description: {
			type: String,
		},
		isOpen: {
			type: Boolean,
			required: true
		}
	},

	methods: {
		handleClose() {
			this.$emit('close')
		}
	}
}
</script>

<style scss src="./PopupWithImage.scss"></style>
