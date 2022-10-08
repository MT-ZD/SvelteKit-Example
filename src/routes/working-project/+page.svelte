<script>
	import { onMount } from 'svelte';

	let audio = new Audio('/beat_three.mp3');

	let paused = true;
	let progress = 0;

	function stopAudio() {
		audio.pause();
		audio.currentTime = 0;
		paused = true;
	}

	function pauseAudio() {
		audio.pause();
		paused = true;
	}

	function playAudio() {
		audio.play();
		paused = false;
	}

	function setProgress() {
		progress = (audio.currentTime / audio.duration) * 100;
		setTimeout(setProgress, 1000);
	}

	onMount(() => {
		setProgress();
	});
</script>

<div class="player">
	<img src="/disk.svg" alt="" class="disk" class:spinning={!paused} />

	<div class="info">
		<div class="title">Beat Three</div>
		<div class="author">Alexander Nakarada</div>
		<div class="controls">
			<div class="track">
				<div class="progress" style="--progress: {progress}%" />
			</div>
			<div class="time">
				<div class="current">00:00</div>
				<div class="total">03:11</div>
			</div>
			<div class="buttons">
				<div class="play">
					<img src="/play.svg" alt="" on:click={playAudio} />
				</div>
				<div class="pause">
					<img src="/pause.svg" alt="" on:click={pauseAudio} />
				</div>
				<div class="stop">
					<img src="/stop.svg" alt="" on:click={stopAudio} />
				</div>
			</div>
		</div>
	</div>
</div>

<svelte:head>
	<title>Music player</title>
</svelte:head>

<style>
	.player {
		padding: 32px;
		background: rgba(255, 255, 255, 0.6);
		border-radius: 12px;
		display: flex;
	}

	.disk {
		animation: spin linear infinite 5s forwards;
		animation-play-state: paused;
	}

	.spinning {
		animation-play-state: running;
	}

	.info {
		margin-left: 24px;
		flex: 1;
		display: flex;
		flex-direction: column;
		justify-content: center;
	}

	.title {
		font-weight: 300;
		font-size: 24px;
	}

	.author {
		font-weight: 300;
		margin-bottom: 24px;
	}

	.track {
		width: 264px;
		height: 2px;
		background: #ffffff;
	}

	.progress {
		width: var(--progress);
		height: 2px;
		background: #514eff;
	}

	.controls {
		color: #fff;
		display: flex;
		flex-direction: column;
	}

	.time {
		width: 100%;
		display: flex;
		justify-content: space-between;
		margin-top: 4px;
		font-size: 12px;
		margin-bottom: 6px;
	}

	.buttons {
		display: flex;
		margin: auto;
	}

	.buttons > div {
		cursor: pointer;
		transition: opacity 0.3s;
	}

	.buttons > div:hover {
		opacity: 0.6;
	}

	.pause {
		margin: 0 16px;
	}

	@keyframes spin {
		from {
			transform: rotate(0deg);
		}
		to {
			transform: rotate(360deg);
		}
	}
</style>
