<template>
	<div style="display: flex; height: 100%; flex-direction: column">
		<nav class="download-bar">
			<a
				:href="googleDriveViewUrl"
				target="_blank"
				class="download"
				style="z-index: 10"
			>
				<div style="display: flex; align-items: center" class="border">
					<img
						src="@/assets/icons/win95/open.png"
						class="icon-image"
						alt="Open Icon"
					/>
					<p style="margin-top: 2px">Open</p>
				</div>
			</a>
			<a
				:href="googleDriveDownloadUrl"
				class="download"
				style="z-index: 10"
				download
			>
				<span style="display: flex" class="border">
					<img src="@/assets/icons/win95/download.png" class="icon-image" />
					<p style="margin-top: 2px">Download</p>
				</span>
			</a>
		</nav>
		<div class="frame" style="z-index: 99">
			<iframe class="frame" :src="googleDriveEmbedUrl"></iframe>
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			googleDriveFileId: "1DR1sctRx6M_qj-_Xv6vGgbOrFULWPpSF",
		};
	},
	computed: {
		googleDriveViewUrl() {
			return `https://drive.google.com/file/d/${this.googleDriveFileId}/view`;
		},
		googleDriveDownloadUrl() {
			return `https://drive.google.com/uc?export=download&id=${this.googleDriveFileId}`;
		},
		googleDriveEmbedUrl() {
			return `https://drive.google.com/file/d/${this.googleDriveFileId}/preview`;
		},
	},
};
</script>

<style scoped>
.download {
	vertical-align: middle;
	box-shadow: 1.5px 1.5px black;
	border-top: solid rgb(250, 250, 250) 1.5px;
	border-left: solid rgb(250, 250, 250) 1.5px;
	border-bottom: solid rgb(90, 90, 90) 1.5px;
	border-right: solid rgb(90, 90, 90) 1.5px;
	background: rgb(192, 192, 192);
	padding: 2px;
	margin-right: 5px;
}

.download:active {
	box-shadow: none;
	background: repeating-conic-gradient(
			rgb(189, 190, 189) 0% 25%,
			rgb(255, 255, 255) 0% 50%
		)
		50% / 2px 2px;
	border-top: solid rgb(0, 0, 0) 1.5px;
	border-left: solid rgb(0, 0, 0) 1.5px;
	border-bottom: solid rgb(250, 250, 250) 1.5px;
	border-right: solid rgb(250, 250, 250) 1.5px;
}

.download-bar {
	border: 1px white solid;
	outline: 1px rgb(123, 125, 123) solid;
	font-size: 12px;
	padding: 4px 4px 4px 4px;
	width: 100%;
	display: flex;
	flex-direction: row;
}

.icon-image {
	width: 15px;
	height: 15px;
	margin-right: 5px;
	margin-top: 0;
	margin-bottom: 0;
}

p {
	cursor: url("../../assets/cursor/pointer.cur"), auto !important;
}

.border {
	justify-content: center;
	align-items: center;
	border: 1px solid transparent;
	font-family: "MS Sans Serif";
	src: url("~@/assets/fonts/MS-Sans-Serif.ttf");
}

.download {
	text-decoration: none;
	color: inherit;
}

.border:active {
	border: black dotted 1px;
}

.download:hover {
	cursor: pointer;
}

.frame {
	width: 100%;
	height: 98%;
}
</style>
