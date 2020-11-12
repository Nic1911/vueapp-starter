<template>
	<div class="about">
		<div class="playgroud" ref="scroller">
			<header class="head" ref="head">HEAD</header>
			<aside class="aside" ref="aside">ASIDE</aside>
			<div class="content" ref="content">
				<section>
					<div class="a box"><span>box</span></div>
				</section>
				<section>
					<div class="b box"><span>box</span></div>
				</section>
				<section>
					<div class="c box"><span>box</span></div>
				</section>
				<section>
					<div class="d box"><span>box</span></div>
				</section>
				<section>
					<div class="e box"><span>box</span></div>
				</section>
				<section>
					<div class="f box"><span>box</span></div>
				</section>
				<section>
					<div class="g box"><span>box</span></div>
				</section>
				<section>
					<div class="h box"><span>box</span></div>
				</section>
				<section>
					<div class="i box"><span>box</span></div>
				</section>
				<section>
					<div class="l box"><span>box</span></div>
				</section>
			</div>
		</div>
	</div>
</template>

<script>
// dependencies
import gsap from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

export default {
	methods: {
		data() {
			return {
				currentSection: 1,
				scrollPercent: 0,
			};
		},
		init() {
			gsap.registerPlugin(ScrollTrigger);
			gsap.utils.toArray("section").forEach((section, index) => {
				const w = section.querySelector(".box");
				// console.log(section);
				const [x, xEnd] =
					index % 2
						? ["100%", (w.scrollWidth - section.offsetWidth) * -1]
						: [w.scrollWidth * -1, 0];

				gsap.to(section, {
					scrollTrigger: {
						trigger: section.querySelectorAll(".box"),
						scrub: true,
						pin: true,
						markers: true,
						start: "center center",
						end: "bottom -100%",
						toggleClass: "active",
						ease: "power2",
					},
				});
			});
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

	section {
		min-height: 25vh;

		&:nth-child(even) {
			background-color: rgba(0, 0, 0, 0.3);
		}
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
