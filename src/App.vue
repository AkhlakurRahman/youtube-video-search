<template>
	<div id="app">
		<div class="header">
			<h3>Youtube Video Viewer</h3>
			<SearchBar @searchInput="onSearchInput" />
		</div>
		<div class="video-section">
			<VideoDetails :video="selectedVideo" />
			<VideoList
				:videos="videos"
				@videoSelect="onVideoSelect"
				class="video-list"
			/>
		</div>
	</div>
</template>

<script>
import axios from 'axios';

import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import VideoDetails from './components/VideoDetails';

export default {
	name: 'app',
	components: {
		SearchBar,
		VideoList,
		VideoDetails
	},
	data() {
		return {
			videos: [],
			selectedVideo: null
		};
	},
	methods: {
		async onSearchInput(searchInput) {
			const res = await axios.get(
				`https://www.googleapis.com/youtube/v3/search`,
				{
					params: {
						key: process.env.VUE_APP_YOUTUBE_API_KEY,
						type: 'video',
						part: 'snippet',
						q: searchInput
					}
				}
			);
			console.log(res.data);
			this.videos = res.data.items;
		},

		onVideoSelect(video) {
			this.selectedVideo = video;
		}
	}
};
</script>

<style>
*,
*::before,
*::after {
	margin: 0;
	padding: 0;
	box-sizing: inherit;
}

html {
	box-sizing: border-box;
	font-size: 62.5%;
}

body {
	font-weight: 300;
	font-family: 'Vollkorn', serif;
	line-height: 1.6;
}

#app {
	max-width: 110rem;
	display: flex;
	margin: 0 auto;
	flex-direction: column;
}
</style>

<style scoped>
.header {
	display: flex;
	justify-content: space-between;
	margin: 2rem 0;
}

h3 {
	font-family: 'Lobster', cursive;
	font-size: 2rem;
}

.video-section {
	display: flex;
	justify-content: space-between;
	margin-top: 3rem;
}

.video-list {
	padding: 0 1rem;
}
</style>
