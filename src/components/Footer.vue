<template>
	<footer class="footer">
		<h5><router-link to="/imprint" class="imprint">Imprint</router-link></h5>
		<div class="popup" @mouseover="popUpFunction()" @mouseout="popUpFunction()">
			<h5>Version {{ this.version }}</h5>
			<span class="popuptext" id="myPopup">Last commit: {{ lastCommit }}</span>
		</div>
		<h5>@2023</h5>
	</footer>
</template>

<script>
import { version as v } from '../../package.json'
import { getLastCommit } from '../services/Footer.Service.js'

export default {
	data() {
		return {
			lastCommit: 'Today',
			version: '',
		}
	},
	methods: {
		popUpFunction() {
			var popup = document.getElementById('myPopup')
			popup.classList.toggle('show')
		},
	},
	async mounted() {
		this.version = v
		this.lastCommit = await getLastCommit()
	},
}
</script>

<style>
.footer {
	display: flex;
	flex-direction: row;
	justify-content: space-evenly;
	background-color: rgb(228, 228, 228);
	border-top: solid 1px rgb(228, 228, 228);
	height: 60px;
}

.popup {
	position: relative;
	display: inline-block;
	cursor: pointer;
	-webkit-user-select: none;
	-moz-user-select: none;
	-ms-user-select: none;
	user-select: none;
}

.popup .popuptext {
	visibility: hidden;
	width: 160px;
	background-color: #555;
	color: #fff;
	text-align: center;
	border-radius: 6px;
	padding: 8px 0;
	position: absolute;
	z-index: 1;
	bottom: 125%;
	left: 50%;
	margin-left: -80px;
}

.popup .popuptext::after {
	content: '';
	position: absolute;
	top: 100%;
	left: 50%;
	margin-left: -5px;
	border-width: 5px;
	border-style: solid;
	border-color: #555 transparent transparent transparent;
}

.popup .show {
	visibility: visible;
	-webkit-animation: fadeIn 1s;
	animation: fadeIn 1s;
	transition-duration: 1s;
	z-index: 10000;
}

@-webkit-keyframes fadeIn {
	from {
		opacity: 0;
	}
	to {
		opacity: 1;
	}
}

@keyframes fadeIn {
	from {
		opacity: 0;
	}
	to {
		opacity: 1;
	}
}
</style>
