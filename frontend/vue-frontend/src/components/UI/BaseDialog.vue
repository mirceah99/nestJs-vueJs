<template>
	<teleport to="body">
		<div class="dialog-bg" @click="$emit('close')"></div>
		<dialog open>
			<header>
				<slot name="header">
					<h2>{{ title }}</h2>
				</slot>
			</header>
			<section>
				<slot> </slot>
			</section>
		</dialog>
	</teleport>
</template>
<script>
export default {
	props: {
		title: {
			type: String,
			required: false,
		},
	},
	emits: ["close"],
};
</script>
<style scoped>
.dialog-bg {
	position: fixed;
	top: 0;
	left: 0;
	height: 100vh;
	width: 100%;
	background-color: rgba(0, 0, 0, 0.75);
	z-index: 10;
}

dialog {
	position: fixed;
	top: 20vh;
	left: 10%;
	width: 80%;
	z-index: 100;
	border-radius: 12px;
	border: none;
	box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
	padding: 0;
	margin: 0;
	overflow: hidden;
}
form {
	padding: 0 20px;
}
header {
	background-color: #42b983;
	color: white;
	width: 100%;
	padding: 1rem;
}

header h2 {
	margin: 0;
}

section {
	padding: 1rem;
}

menu {
	padding: 1rem;
	display: flex;
	justify-content: flex-end;
	margin: 0;
}

@media (min-width: 768px) {
	dialog {
		left: calc(50% - 40vw);
		width: 80vw;
	}
}
</style>
