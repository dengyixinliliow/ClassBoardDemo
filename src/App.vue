<script>
import Class from './components/Class.vue';

export default {
	components: {
		Class,
	},
	data() {
		return {
			classes: [
				{
					id: 1,
					title: 'first class',
					date: '11/01',
					time: '10:30AM',
					peroid: '11/01-11/06',
					description: 'This class talks about the math',
					author: 'alice, bob, cindy',
					collection_num: 25,
				},
				{
					id: 2,
					title: 'second class - Let us try something interesting!',
					date: '11/02',
					time: '10:30AM',
					peroid: '11/02-11/10',
					description: 'This class talks about the english',
					author: 'alice, bob, cindy',
					collection_num: 23,
				},
				{
					id: 3,
					title: 'third class',
					date: '11/02',
					time: '10:30AM',
					peroid: '11/02-11/11',
					description:
						'This class talks about the music.music, art concerned with combining vocal or instrumental sounds for beauty of form or emotional expression, usually according to cultural standards of rhythm, melody, and, in most Western music, harmony.',
					collection_num: 0,
				},
				{
					id: 4,
					title: 'fourth class',
					date: '11/03',
					time: '10:30AM',
					peroid: '11/01-11/06',
					description: 'This class talks about the math',
					author: 'alice',
					collection_num: 3,
				},
				{
					id: 5,
					title: 'fifth class',
					date: '11/05',
					time: '10:30AM',
					peroid: '11/02-11/10',
					description: 'This class talks about the englisj',
					collection_num: 29,
				},
				{
					id: 6,
					title: 'sixth class',
					date: '11/08',
					time: '10:30AM',
					peroid: '11/02-11/11',
					description: 'This class talks about the music',
					collection_num: 3,
				},
			],
		};
	},

	methods: {
		scrollLeft() {
			const slider = this.$refs.slider;
			// container.scrollLeft -= 300
			let scrollAmount = 0;
			let slideTimer = setInterval(function () {
				console.log('yesy');
				slider.scrollLeft -= 10;
				scrollAmount += 10;
				if (scrollAmount >= 200) {
					window.clearInterval(slideTimer);
				}
			}, 25);
		},
		scrollRight() {
			const slider = this.$refs.slider;
			let scrollAmount = 0;
			let slideTimer = setInterval(function () {
				console.log('yesy');
				slider.scrollLeft += 10;
				scrollAmount += 10;
				if (scrollAmount >= 200) {
					window.clearInterval(slideTimer);
				}
			}, 25);
		},
	},
};
</script>

<template>
	<div class="header">
		<div class="header-title">课程预告</div>
		<button class="calendar_btn">查看课程时间</button>
	</div>

	<div class="container">
		<div class="slider" ref="slider">
			<Class
				v-for="class_item in classes"
				:key="class_item.id"
				:title="class_item.title"
				:date="class_item.date"
				:time="class_item.time"
				:period="class_item.peroid"
				:description="class_item.description"
				:author="class_item.author"
				:collection_num="class_item.collection_num"
			></Class>
		</div>
		<button class="scroll_btn prev" @click="scrollLeft">
			<font-awesome-icon icon="chevron-left" />
		</button>
		<button class="scroll_btn next" @click="scrollRight">
			<font-awesome-icon icon="chevron-right" />
		</button>
	</div>
</template>

<style>
.container {
	width: 90%;
	position: relative;
	margin: 1rem;
}

.slider {
	margin: 1rem;
	width: 100%;
	display: flex;
	flex-direction: row;
	overflow-x: scroll;
}

.slider::-webkit-scrollbar {
	display: none;
}

header {
	display: flex;
}

button,
.header-title {
	display: inline;
}

.header-title {
	margin-left: 1rem;
	font-size: 2.25rem;
	font-weight: bolder;
}

.calendar_btn {
	background-color: #1e90ff;
	border: 0.1rem solid #ffffff;
	border-radius: 0.4rem;
	padding: 0.5rem 1rem;
	color: #ffffff;
	cursor: pointer;
}

.calendar_btn:hover {
	background-color: #0000ff;
}

.scroll_btn {
	position: absolute;
	top: 50%;
	background-color: #ffffff;
	border: 0.1rem solid #ffffff;
	border-radius: 0.25rem;
	cursor: pointer;
}

.prev {
	left: 0;
	margin-left: 2rem;
}

.next {
	right: 0;
}
</style>
