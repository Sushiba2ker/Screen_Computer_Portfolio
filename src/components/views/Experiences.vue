<template>
	<div>
		<div v-if="!hideHeader" class="header">
			<img
				class="header-img"
				:src="getImageSrc('experiences.png', true)"
				alt="Experiences Image"
			/>
			<h3 class="header-title">{{ headingTitle }}</h3>
			<h4 class="header-subtitle">{{ headingSubtitle }}</h4>
		</div>
		<hr />

		<div class="tabs">
			<div
				class="tab"
				:class="{ 'active-tab first': activeTab === 'professional' }"
				@click="setActiveTab('professional')"
			>
				Professional
			</div>
			<div
				class="tab"
				:class="{ 'active-tab': activeTab === 'organizational' }"
				@click="setActiveTab('organizational')"
			>
				Organizational
			</div>
			<div
				class="tab"
				:class="{ 'active-tab': activeTab === 'volunteer' }"
				@click="setActiveTab('volunteer')"
			>
				Volunteer
			</div>
		</div>

		<div v-if="activeTab === 'professional'" class="content">
			<div v-for="(professional, index) in professionals" :key="index">
				<div class="container">
					<div class="title">
						<img class="img" :src="getImageSrc(professional.image)" />
						<p class="name">{{ professional.company }}</p>
					</div>
				</div>
				<div class="desc">
					<p class="role">
						{{ professional.position }}
						<span class="year">{{ professional.duration }}</span>
					</p>
					<!-- <p class="paragraph">{{ professional.description }}</p> -->
					<ul>
						<li
							v-for="(responsibility, index) in professional.responsibilities"
							:key="index"
						>
							{{ responsibility }}
						</li>
					</ul>
				</div>
				<hr />
			</div>
		</div>

		<div v-if="activeTab === 'organizational'" class="content">
			<div v-for="(organizational, index) in organizationals" :key="index">
				<div class="container">
					<div class="title">
						<img class="img" :src="getImageSrc(organizational.image)" />
						<p class="name">{{ organizational.company }}</p>
					</div>
				</div>
				<div class="desc">
					<p class="role">
						{{ organizational.position }}
						<span class="year">{{ organizational.duration }}</span>
					</p>
					<!-- <p class="paragraph">{{ organizational.description }}</p> -->
					<ul>
						<li
							v-for="(responsibility, index) in organizational.responsibilities"
							:key="index"
						>
							{{ responsibility }}
						</li>
					</ul>
				</div>
				<hr />
			</div>
		</div>

		<div v-if="activeTab === 'volunteer'" class="content">
			<div v-for="(volunteer, index) in volunteers" :key="index">
				<!-- <div class="container">
          <div class="title">
            <img class="img" :src="getImageSrc(volunteer.image)">
            <p class="name">{{ volunteer.company }}</p>
          </div>
        </div> -->
				<div class="desc">
					<p class="event">{{ volunteer.event }}</p>
					<p class="role">
						{{ volunteer.position }}
						<span class="year">{{ volunteer.duration }}</span>
					</p>
					<!-- <p class="paragraph">{{ volunteer.description }}</p> -->
					<ul>
						<li
							v-for="(responsibility, index) in volunteer.responsibilities"
							:key="index"
						>
							{{ responsibility }}
						</li>
					</ul>
				</div>
				<hr />
			</div>
		</div>
	</div>
</template>

<script>
export default {
	props: {
		hideHeader: {
			type: Boolean,
			default: false,
		},
	},
	data() {
		return {
			headingTitle: "Experiences",
			headingSubtitle: "My Professional/Organizational Experiences",
			activeTab: "professional",
			professionals: [
				{
					image: "freelance.jpeg",
					company: "Freelance",
					position: "Data Engineer / Software Developer",
					duration: "September 2021 - Present",
					responsibilities: [
						"Designed and developed scalable data pipelines using Python and SQL for processing ETL tasks for various clients, enhancing data accessibility and reliability.",
						"Optimized databases and data warehouses, ensuring data integrity, security, and efficient query performance.",
						"Delivered high-quality code and data solutions for over 10 projects, achieving a 98% customer satisfaction rate and improving project performance by 20%.",
					],
				},
				{
					image: "bidv.jpg",
					company: "Bank for Investment and Development of Vietnam (BIDV)",
					position: "Intern",
					duration: "February 2024 - May 2024",
					responsibilities: [
						"Assisted in the development and optimization of data pipelines to process large volumes of financial data, increasing processing speed by 25%.",
						"Contributed to designing and implementing a Monthly Attendance Automation System, reducing HR administrative work by 40%.",
						"Supported the development and deployment of a contract punching system, optimizing contract management processes and improving data accuracy.",
					],
				},
			],
			organizationals: [],
			volunteers: [],
		};
	},
	methods: {
		setActiveTab(tab) {
			this.activeTab = tab;
		},
		getImageSrc(imageName, isHeaderImage = false) {
			if (!imageName) {
				return null;
			}
			let imagePath;
			try {
				if (isHeaderImage) {
					imagePath = require("@/assets/icons/win95/" + imageName);
				} else {
					imagePath = require("@/assets/images/experiences/professional/" +
						imageName);
				}
			} catch (error) {
				console.warn(`Image not found: ${imageName}`);
				return null; // Hoặc trả về một hình ảnh mặc định
			}
			return imagePath;
		},
	},
};
</script>

<style scoped>
/* Content */
.content {
	border-top: solid rgb(250, 250, 250) 3px;
	border-left: solid rgb(250, 250, 250) 3px;
	border-bottom: solid rgb(90, 90, 90) 3px;
	border-right: solid rgb(90, 90, 90) 3px;
	padding: 10px;
	margin-top: -3px;
	position: relative;
	z-index: 1;
}

.container {
	display: flex;
	justify-content: center;
}

.title {
	display: inline-block;
	text-align: center;
	padding: 20px 0 5px 0;
}

.img {
	width: 130px;
}

.name {
	font-weight: bold;
	text-align: center;
	margin-bottom: 0;
}

.event {
	text-align: center;
	font-weight: bold;
}

.desc {
	padding: 0 30px 0 30px;
	font-size: 15px;
}

.role {
	font-style: italic;
}

.year {
	float: right;
	font-size: 14px;
	font-style: normal;
}

.paragraph {
	text-align: justify;
	line-height: 1.3;
}

.desc li {
	list-style: square;
	margin-bottom: 5px;
}

@media screen and (max-width: 1024px) {
	/* Content */
	.content {
		border-top: solid rgb(250, 250, 250) 2px;
		border-left: solid rgb(250, 250, 250) 2px;
		border-bottom: solid rgb(90, 90, 90) 2px;
		border-right: solid rgb(90, 90, 90) 2px;
		padding: 10px;
		margin-top: -2px;
		position: relative;
		z-index: 1;
	}

	.container {
		margin-bottom: 0;
	}

	.desc {
		margin-top: 0;
	}

	.role {
		display: flex;
		flex-direction: column;
		justify-content: center;
		text-align: center;
		line-height: 1.3;
		padding: 0 0 15px 0;
		margin-top: 0;
	}

	.name {
		margin-top: 15px;
	}

	.desc {
		padding: 10px;
	}
}
</style>
