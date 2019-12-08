<template>
	<div v-if="video">
		<div class="video-player" style="--aspect-ratio: 16/9;">
			<iframe
				:src="videoUrl"
				width="1600"
				height="900"
				frameborder="0"
				allowfullscreen
			></iframe>
		</div>
		<div class="video-details">
			<h4>{{ video.snippet.title }}</h4>
			<p>{{ video.snippet.description }}</p>
		</div>
	</div>
</template>

<script>
export default {
	name: 'VideoDetails',
	props: ['video'],
	computed: {
		videoUrl() {
			const { videoId } = this.video.id;
			return `https://www.youtube.com/embed/${videoId}`;
		}
	}
};
</script>

<style scoped>
.video-details {
	margin: 2rem 0rem;
}

h4 {
	font-size: 1.8rem;
}

p {
	font-size: 1.6rem;
}

[style*='--aspect-ratio'] > :first-child {
	width: 100%;
}
[style*='--aspect-ratio'] > img {
	height: auto;
}
@supports (--custom: property) {
	[style*='--aspect-ratio'] {
		position: relative;
	}
	[style*='--aspect-ratio']::before {
		content: '';
		display: block;
		padding-bottom: calc(100% / (var(--aspect-ratio)));
	}
	[style*='--aspect-ratio'] > :first-child {
		position: absolute;
		top: 0;
		left: 0;
		height: 100%;
	}
}
</style>
