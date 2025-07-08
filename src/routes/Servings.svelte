<script>
	import '../servings.css';
	import jrice from '$lib/images/jrice.svg';
	import protein from '$lib/images/protein.svg';
	import side from '$lib/images/side.svg';
	import sauce from '$lib/images/sauce.svg';
	import garnish from '$lib/images/garnish.svg';
	import left from '$lib/images/left.svg';
	import right from '$lib/images/right.svg';

	let images = [
		{ src: jrice, caption: 'Start with a base', color: '#EE3300' },
		{ src: protein, caption: 'Choose protein', color: '#4C0703' },
		{ src: sauce, caption: 'Add sauce', color: '#FBAB1E' },
		{ src: side, caption: 'Pick sides', color: '#104E44' },
		{ src: garnish, caption: 'Garnish & Finish', color: '#EA6113' }
	];
	let current = $state(0);
	let touchStart = $state(0);
	let touchEnd = $state(0);
	const minSwipeDistance = 50;

	function prev() {
		current = (current - 1 + images.length) % images.length;
	}

	function next() {
		current = (current + 1) % images.length;
	}

	function handleTouchStart(e) {
		touchEnd = null;
		touchStart = e.touches[0].clientX;
	}

	function handleTouchMove(e) {
		touchEnd = e.touches[0].clientX;
	}

	function handleTouchMoveEnd() {
		if (!touchEnd || !touchStart) return;
		const distance = touchEnd - touchStart;
		const isLeftSwipe = distance < -minSwipeDistance;
		const isRightSwipe = distance > minSwipeDistance;
		if (isLeftSwipe) {
			next();
		} else if (isRightSwipe) {
			prev();
		}
	}

	function handleKeyDown(e) {
		if (e.key === 'ArrowLeft') {
			prev();
		} else if (e.key === 'ArrowRight') {
			next();
		}
	}
</script>

<svelte:window onkeydown={handleKeyDown} />

<div class="carousel mobile mb-4">
	<div
		class="carousel-content rounded-2xl border-white bg-white shadow-lg"
		ontouchstart={handleTouchStart}
		ontouchmove={handleTouchMove}
		ontouchend={handleTouchMoveEnd}
		aira-label="Image Carousel"
	>
		<img
			src={images[current].src}
			alt={images[current].caption}
			class="m-4 transition-transform duration-700 hover:scale-105"
		/>
		<div
			class="caption transition-all duration-200 hover:opacity-90"
			style="background:{images[current].color}"
		>
			{images[current].caption}
		</div>
		<div class="btns">
			<button class="nav left" onclick={prev} aria-label="Previous">&#8592;</button>
			<button class="nav right" onclick={next} aria-label="Next">&#8594;</button>
		</div>
	</div>
</div>

<div class="menu desktop display flex items-center">
	<div class="menu-item">
		{#each images as image, index (index)}
			<div class="carousel-content">
				<img src={image.src} alt={image.caption} class="menu-img" />
				<div class="caption" style="background:{image.color}; cursor:pointer">{image.caption}</div>
			</div>
		{/each}
	</div>
</div>
