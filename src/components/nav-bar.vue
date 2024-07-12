<template>
	<nav>
		<div class="container">
			<div class="name">
				<img class="logo" src="../assets/logo.png" alt="logo vue">
				<h1 class="title">Reddit</h1>
			</div>
			<div class="search-bar">
				<img class="icon" src="../assets/search.png" alt="">
				<input type="search" placeholder="Buscar en Reddit">
			</div>
			<div class="button">
				<button class="btn" @click="deleteAllPosts">
					<img class="qr-code" src="../assets/qrcode.png" alt="">
					<span class="title">Eliminar</span>
				</button>
				<a @click="reloadPosts"> Refrescar</a>
			</div>
		</div>
		<hr class="line-bottom">
	</nav>

</template>
<script>
export default {
    name: 'NavBarComponent',
	methods: {
    deleteAllPosts() {
      this.$emit('delete-all-posts');
    },
    reloadPosts() {
      this.$emit('reload-posts');
    }
  }
}
</script>

<style scoped>
.container {
	width: 100%;
	margin: 0 auto;
}

nav {
	width: 100%;
	padding: 10px;
	position: fixed;
	top: 0;
	z-index: 10;
	background-color: #0F1114;
}

.line-bottom {
	border: none;
	height: 1px;
	background: rgba(255, 255, 255, 0.1);
	margin-top: 10px;
}

nav .container {
	display: flex;
	align-items: center;
	justify-content: space-between;
}

.search-bar {
	display: flex;
	justify-content: center;
	background-color: #2B3236;
	border-radius: 2rem;
	padding: 0.6rem 1rem;
}

.icon {
	width: 16px;
	height: 16px;
	background-color: #2B3236;
	color: #8BA2AD;
}

.search-bar input {
	background: transparent;
	width: 30vw;
	margin-left: 0.5rem;
	font-size: 0.9rem;
	color: #8BA2AD;
}

.button {
	display: flex;
	align-items: center;
	gap: 14px;
}

.btn {
	display: flex;
	align-items: center;
	padding: 10px;
	font-size: 16px;
	border-radius: 20px;
	border: 1px solid #2A3236;
	background-color: #2A3236;
	cursor: pointer;
}

.button a {
	padding: 10px;
	text-decoration: none;
	border: 1px solid #D93900;
	border-radius: 20px;
	background-color: #D93900;
	cursor: pointer;
}

.qr-code {
	width: 16px;
	height: 16px;
	background-color: #2A3236;
	margin-right: 5px;
}

.name {
	display: flex;
	justify-content: center;
	align-content: center;
	gap: 10px;
}

.logo {
	width: 32px;
	height: 32px;
}

@media (min-width: 320px) and (max-width: 768px) {
	.title {
		display: none;
	}

	.btn {
		justify-content: center;
	}
}

</style>