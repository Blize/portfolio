<template>
	<div class="parent-home">
		<div class="first-info">
			<h1 class="title">Blize</h1>
			<div class="parent-animation-under-title">
				<div class="fly-in-title"><h2>I love</h2></div>

				<div class="fly-in-under-title" :class="{ hidden: isNotActive }">
					<h2>{{ chosenTitle }}</h2>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	data() {
		return {
			title: ['coding', 'designing', 'drawing', 'creating', 'biking', 'gaming'],
			chosenTitle: '',
			isNotActive: true,
		}
	},
	mounted() {
		this.changeTitle()
		setTimeout(() => {
			this.isNotActive = false
		}, 500)
	},
	methods: {
		changeTitle() {
			this.chosenTitle = this.title[Math.floor(Math.random() * this.title.length)]
			window.setInterval(() => {
				this.chooseRandomTitle()
			}, 3000)
		},
		chooseRandomTitle() {
			this.chosenTitle = this.title[Math.floor(Math.random() * this.title.length)]
		},
	},
}
</script>

<style scoped>
div.parent-home {
	display: flex;
	align-items: flex-start;
	justify-content: center;
	gap: 4rem;

	margin: 1rem;

	height: 100vh;
}
.first-info {
	display: flex;
	flex-direction: column;
}
.title {
	font-size: 5rem;
	margin-bottom: -1rem;
}
.parent-animation-under-title {
	display: flex;
	flex-direction: row;
}
.fly-in-title {
	padding-left: -0.25rem;
}
.fly-in-under-title {
	padding-left: 0.25rem;
	opacity: 1;
	transition: all 0.5s ease-out;
}
.fly-in-under-title.hidden {
	opacity: 0;
	transform: translateY(50px);
}
</style>
