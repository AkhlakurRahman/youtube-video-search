<template>
	<div class="video-wrapper">
		<h3>Search Results</h3>
		<VideoListItem
			v-for="video in videos"
			:key="video.etag"
			:video="video"
		></VideoListItem>
	</div>
</template>

<script>
import VideoListItem from './VideoListItem';

export default {
	name: 'VideoList',
	components: {
		VideoListItem
	},
	props: {
		videos: Array
	}
};
</script>

<style scoped>
.video-wrapper {
	width: 75rem;
	margin: auto;
	display: flex;
	flex-direction: column;
}

h3 {
	font-size: 2rem;
	border-bottom: 1px solid #191919;
	margin-bottom: 2rem;
}
</style>
