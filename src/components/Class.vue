<script>
export default {
	props: [
		'title',
		'date',
		'time',
		'period',
		'description',
		'author',
		'collection_num',
	],
	data() {
		return {
			collected: false,
			reserved: false,
		};
	},

	computed: {
		countCollection() {
			if (this.collected) {
				return this.collection_num + 1;
			} else {
				return this.collection_num;
			}
		},
	},

	methods: {
		onCollectClicked() {
			if (this.collected) {
				alert('取消收藏成功');
				this.collected = false;
			} else {
				alert('收藏成功');
				this.collected = true;
			}
		},
		onReserveClicked() {
			if (this.reserved) {
				alert('取消预约成功');
				this.reserved = false;
			} else {
				alert('预约成功');
				this.reserved = true;
			}
		},
	},
};
</script>

<template>
	<!-- container -->
	<div class="class-board">
		<!-- Info -->
		<div>
			<div>
				<span class="date">{{ date }}</span
				><span class="time">{{ time }}</span>
			</div>
			<div class="period">{{ period }}</div>
		</div>
		<!-- Card -->
		<div class="class-card">
			<div class="class-img">
				<p class="class-description">{{ description }}</p>
				<div class="class-btn">
					<button @click="onReserveClicked" class="class-reserve">
						<font-awesome-icon icon="check-circle" />
					</button>
					<button @click="onCollectClicked" class="class-collect">
						<font-awesome-icon icon="star" />
					</button>
				</div>
			</div>
			<div class="class-title">{{ title }}</div>
			<div class="collection">
				<font-awesome-icon
					icon="star"
					:class="[collected ? 'icon-active' : 'icon']"
				/>
				<span>{{ countCollection }}</span>
			</div>
		</div>
	</div>
</template>

<style>
.date {
	font-size: 2rem;
	color: #1e90ff;
}

.time {
	margin-left: 0.25rem;
}

.period {
	color: #808080;
	margin: 0.5rem 0;
}

.class-title {
	font-size: 1.25rem;
	max-height: 2rem;
	margin: 1rem;
	margin-top: 0.5rem;
	white-space: nowrap;
	overflow: hidden;
	text-overflow: ellipsis;
}

.icon {
	color: #dedede;
}

.icon-active {
	color: #e69b00;
}

.icon:hover {
	cursor: pointer;
}

.class-board {
	display: inline;
	width: 18.75rem;
	margin: 0.625rem;
}

.class-btn {
	position: absolute;
	bottom: 0.2rem;
	right: 0.2rem;
}

.class-reserve,
.class-collect {
	margin: 0.1rem;
	background-color: #ffffff;
	border: 0.1rem solid #ffffff;
	border-radius: 0.25rem;
	cursor: pointer;
}

.class-card {
	position: relative;
	border-radius: 0.5rem;
	background-color: #fff;
	box-shadow: 0.05rem 0.1rem 0.3rem -0.03rem rgba(0, 0, 0, 0.45);
	width: 18.75rem;
	height: 15rem;
}

.class-img {
	display: flex;
	align-items: center;
	justify-content: center;
	border-radius: 0.5rem;
	box-shadow: 0.05rem 0.1rem 0.3rem -0.03rem rgba(0, 0, 0, 0.45);
	background-color: #1e90ff;
	width: 100%;
	height: 10rem;
	position: relative;
}

.class-description {
	margin: 3rem;
	overflow: hidden;
	text-overflow: ellipsis;
	display: -webkit-box;
	-webkit-line-clamp: 5;
	-webkit-box-orient: vertical;
}

.collection {
	position: absolute;
	right: 0.625rem;
}
</style>
