<template>
	<div class="video-list">
		<img :src="thumbnailUrl" :alt="video.snippet.title" />
		<div class="video-details">
			<h4>{{ video.snippet.title }}</h4>
			<h5>{{ video.snippet.channelTitle }}</h5>
			<p>{{ video.snippet.description }}</p>
		</div>
	</div>
</template>

<script>
export default {
	name: 'VideoListItem',
	props: {
		video: Object
	},
	computed: {
		thumbnailUrl() {
			return this.video.snippet.thumbnails.default.url;
		}
	}
};
</script>

<style scoped>
.video-list {
	display: flex;
	align-items: flex-start;
	margin-bottom: 2rem;
	padding: 1.5rem 1.2rem;
}

.video-list:hover {
	cursor: pointer;
	background: #eee;
}

.video-details {
	margin-left: 2rem;
}

h4 {
	font-size: 1.8rem;
}

h5 {
	font-size: 1.4rem;
}

p {
	font-size: 1.5rem;
}
</style>
