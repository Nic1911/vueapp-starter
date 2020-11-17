<template>
	<div class="about">
		<div class="playgroud" ref="scroller">
			<header class="head" ref="head">{{ data.headTitle }}</header>
			<aside class="aside" ref="aside">{{ data.asideTitle }}</aside>
			<div class="content" ref="content">
				<div class="content__hero">
					<h1>{{ data.contentTitle }}</h1>
					<img
						v-if="data.cover"
						class="project-block-gallery__slide-img"
						:srcset="
							`${data.cover.src640} 640w, ${data.cover.src768} 768w, ${data.cover.src1200} 1200w, ${data.cover.src1920} 1920w`
						"
						:alt="data.cover.title"
					/>
				</div>
				<section class="section">
					<div class="a box"><span>box a</span></div>
				</section>
				<section class="section">
					<div class="b box"><span>box b</span></div>
				</section>
				<section class="section">
					<div class="c box"><span>box c</span></div>
				</section>
				<section class="section">
					<div class="d box"><span>box d</span></div>
				</section>
				<section class="section">
					<div class="e box"><span>box e</span></div>
				</section>
				<section class="section">
					<div class="f box"><span>box f</span></div>
				</section>
				<section class="section">
					<div class="g box"><span>box g</span></div>
				</section>
				<section class="section">
					<div class="h box"><span>box h</span></div>
				</section>
				<section class="section">
					<div class="i box"><span>box i</span></div>
				</section>
				<section class="section">
					<div class="l box"><span>box l</span></div>
				</section>
			</div>
		</div>
	</div>
</template>

<script>
// data
import data from "@/data/about.json";
// dependencies
import gsap from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

export default {
	data() {
		return {
			currentSection: 1,
			scrollPercent: 0,
			// data
			data: null,
		};
	},
	created() {
		this.data = data;
	},
	methods: {
		init() {
			gsap.registerPlugin(ScrollTrigger);

			gsap.to(".box.a", {
				// x: +400,
				// rotate: 90,
				scrollTrigger: {
					trigger: ".box.a",
					// pin: true,
					start: "top bottom",
					end: `bottom top`,
					scrub: 1,
					markers: true,
				},
			});
			// gsap.utils.toArray("section").forEach((section, index) => {
			// 	const w = section.querySelector(".box");
			// 	console.log(w);
			// 	console.log(section);
			// 	const [x, xEnd] =
			// 		index % 2
			// 			? ["100%", (w.scrollWidth - section.offsetWidth) * -1]
			// 			: [w.scrollWidth * -1, 0];

			// 	gsap.to(w, {
			// 		// x: 400,
			// 		scrollTrigger: {
			// 			trigger: section,
			// 			scrub: true,
			// 			// pin: true,
			// 			markers: true,
			// 			start: "top top",
			// 			end: `bottom 100px`,
			// 		},
			// 	});
			// });
		},
	},
	mounted() {
		this.$nextTick(() => {
			this.init();
		});
	},
};
</script>

<style lang="scss">
.playgroud {
	width: 100%;
	min-height: 100vh;
	max-width: 1340px;
	margin: 0 auto;

	display: grid;
	grid-gap: 10px;

	grid-template-rows: 100px auto;
	grid-template-columns: 0.5fr 2fr;
}

.section {
	min-height: 30vh;

	&:nth-child(even) {
		background-color: rgba(148, 236, 130, 0.76);
	}
}

.head {
	display: flex;
	align-items: center;
	justify-content: center;
	background-color: $color-button-disabled-bg;
	grid-area: 1 / 1 / 2 / 3;
}
.aside {
	display: flex;
	align-items: center;
	justify-content: center;
	background-color: $color-input-border;
	grid-area: 2 / 1 / 2 / 2;
}
.content {
	display: grid;
	grid-template-columns: 100%;
	grid-template-rows: repeat(10, auto);
	column-gap: 10px;
	row-gap: 15px;

	grid-area: 2 / 2 / 2 / 3;

	&__hero {
		min-height: 20vh;
	}
}

.box {
	width: 50px;
	height: 50px;
	display: flex;
	align-items: center;
	justify-content: center;

	background-color: $color-heading-text;
}
.a {
	background-color: lightblue;
}
.b {
	background-color: lightcoral;
}
.c {
	background-color: lightcyan;
}
.d {
	background-color: lightgoldenrodyellow;
}
.e {
	background-color: lightgray;
}
.f {
	background-color: lightpink;
}
.g {
	background-color: lightsalmon;
}
.h {
	background-color: lightseagreen;
}
.i {
	background-color: lightsteelblue;
}
.l {
	background-color: lightyellow;
}
</style>
