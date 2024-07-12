<template>
	<div class="conteiner">
		<div class="card">
			<div class="top">
				<div class="user-details">
					<div class="profile-img">
						<img :src="post.avatar" alt="avatar">
					</div>
					<h3>{{ post.name }}<span class="time"> <span class="ball">•</span> hace {{ post.time }}</span></h3>
				</div>
				<div @click="removePost">
					<img class="dot" src="../assets/trash.png" alt="">
				</div>
			</div>
			<div class="description">
				<h2>{{ post.message }}</h2>
			</div>
			<div class="imgBX">
				<img :src="post.image" alt="post image">
			</div>
			<div class="action-btns">
				<button>
					<img class="img-up" src="../assets/arrow-big-up.png" alt="up">
					<span>{{ post.likes }}</span>
					<img class="img-down" src="../assets/arrow-big-down.png" alt="down">
				</button>
				<button>
					<img src="../assets/message.png" alt="msg">
					<span>{{ post.messages }}</span>
				</button>
				<button>
					<img src="../assets/share.png" alt="share">
					<span>compartir</span>
				</button>
			</div>
		</div>
		<hr class="line">
	</div>
</template>

<script>
export default {
  name: 'CardComponent',
  props: {
    post: {
      type: Object,
      required: true
    },
    index: {
      type: Number,
      required: true
    }
  },
  methods: {
    removePost() {
      this.$emit('remove-post', this.index);
    }
  }
}
</script>

<style scoped>
.line {
	border: none;
	height: 1px;
	background: rgba(255, 255, 255, 0.1);
	margin: 5px 0;
}

.card {
	position: relative;
	padding: .25rem 1rem .25rem 1rem;
	margin-top: .25rem;
	margin-bottom: .25rem;
	border-radius: 16px;
	width: auto;
	max-width: 760px;
	min-height: auto;
	background-color: #0E1113;
	cursor: pointer;
}

.card:hover {
	background-color: #343a3e;
	transition: background-color 0.3s ease-in-out;
}

.card:hover *{
	background-color: inherit;
}

.card .top {
	display: flex;
	justify-content: space-between;
	align-items: center;
}

.card .top .user-details {
	display: flex;
	align-items: center;
}

.card .top .user-details .profile-img {
	position: relative;
	width: 24px;
	height: 24px;
	border-radius: 50%;
	overflow: hidden;
	margin-right: 4px;
}

.card .top .user-details .profile-img img {
	width: 24px;
	height: 24px;
}


.card .top .user-details h3 {
	font-size: .75rem;
	color: #B7C4D4;
	font-weight: 600;
	line-height: 1rem;
}

.card .top .user-details h3 span {
	font-size: .75rem;
	line-height: 1rem;
	margin-left: 5px;
	color: #8BA2AD;
}

.card .top .user-details h3 span .ball {
	margin: 0 5px;
}

.dot {
	width: 16px;
	height: 16px;
	cursor: pointer;
}

.dot:hover {
	border-radius: 50%;
	background-color: #f6561c;
}

.description {
	display: flex;
	flex-direction: column;
	flex-grow: 1;
	max-width: 100%;
	margin-bottom: .5rem;
}

.description h2 {
	font-size: 1.125rem;
	line-height: 1.5rem;
	color: #eef1f3;
}

.imgBX {
	position: relative;
	display: flex;
	justify-content: center;
	align-items: center;
	width: 100%;
	height: auto;
	margin: 10px 0 15px;
	border: 2px solid rgba(255, 255, 255, 0.1);
	border-radius: 16px;
}

.imgBX img {
	border-radius: 16px;
}

.action-btns {
	display: flex;
	justify-content: flex-start;
	align-items: center;
	gap: 12px;
}

.action-btns button {
 padding: 8px 12px;
 font-size: 12px;
 background-color: #333D41;
 color: #eef1f3;
 border-radius: 16px;
 display: flex;
 align-items: center;
 gap: 6px;
 cursor: pointer;
}

.action-btns button:hover {
	background-color: #385c6b;
}

.action-btns button img {
	width: 16px;
	height: 16px;
	border-radius: 50%;
	background-color: transparent;
	color: #DBE4E9;
}

@media (min-width: 320px) and (max-width: 768px) {
  .card {
    max-width: 300px;
  }

  .description h2 {
	font-size: 12px;
	line-height: 1rem;
  }

  .imgBX {
	overflow: hidden;
  }

  .imgBX img {
	width: auto;
	height: auto;
  }
}

</style>