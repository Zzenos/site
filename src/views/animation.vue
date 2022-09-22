<template>
	<div class="animation">
		<div class="container">
			<!-- <div class="item" style="--color: #00ade1" data-text="Home">Home</div>
			<div class="item" style="--color: #ff6493">About</div>
			<div class="item" style="--color: #ffdd1c">Service</div>
			<div class="item" style="--color: #00dc82">Team</div>
			<div class="item" style="--color: #dc00d4">Contact</div> -->
			<template v-for="(item, index) in data" :key="index">
				<div class="item" :style="{'--color': item.color}" :data-text="item.text">{{ item.text }}</div>
			</template>
		</div>
	</div>
</template>
<script setup lang="ts">
	// const color1 = '#00ade1'
	const data = [
		{
			color: '#00ade1',
			text: 'Home'
		},
		{
			color: '#ff6493',
			text: 'About'
		},
		{
			color: '#ffdd1c',
			text: 'Service'
		},
		{
			color: '#00dc82',
			text: 'Team'
		},
		{
			color: '#dc00d4',
			text: 'Contact'
		},
	]
</script>
<style lang="scss">
.animation {
	.container {
		width: 100%;
		height: 800px;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		background-color: #252839;
		.item {
			width: 400px;
			margin-top: 50px;
			font-size: 5em;
			letter-spacing: 2.5px;
			text-align: left;
			text-transform: uppercase;
			color: transparent;
			position: relative;
			-webkit-text-stroke: 1px rgba(255, 255, 255, 0.5);
			&::before {
				content: attr(data-text);
				position: absolute;
				left: -10px;
				width: 0;
				color: var(--color);
				overflow: hidden;
				transition: 1s;
				border-right: 4px solid var(--color);
				-webkit-text-stroke: 1px var(--color);
			}
			&:hover {
				&::before {
					width: 100%;
					left: 0px;
					filter: drop-shadow(0 0 25px var(--color));
				}
			}
		}
	}
}
</style>
