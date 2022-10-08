<div class="player">
	<img src="/disk.svg" alt="" />

	<div class="info">
		<div class="title">Beat Three</div>
		<div class="author">Alexander Nakarada</div>
		<div class="controls">
			<div class="track">
				<div class="progress" style="--progress: 20%" />
			</div>
			<div class="time">
				<div class="current">00:00</div>
				<div class="total">03:11</div>
			</div>
			<div class="buttons">
				<div class="play">
					<img src="/play.svg" alt="" />
				</div>
				<div class="pause">
					<img src="/pause.svg" alt="" />
				</div>
				<div class="stop">
					<img src="/stop.svg" alt="" />
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

	.spinning {
		animation: spin linear infinite 5s;
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
