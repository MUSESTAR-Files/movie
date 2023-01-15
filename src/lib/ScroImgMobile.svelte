<script>
	import {onDestroy, onMount} from 'svelte';
	import {tweened} from 'svelte/motion';
	import {cubicInOut} from 'svelte/easing';

	export let width = 190;

	export let imgList = [

	];
	const twYCer = tweened(0, {
		duration: 1200,
		easing: cubicInOut
	});
	let isCov = false;
	let intervalID = null;
	onMount(() => {
		TheTimer();
		intervalID = setInterval(() => {
			if (isCov) {
				twYCer.set(0, {duration: 0});
				TheTimer();
			} else {
				twYCer.set(width);
			}
			isCov = !isCov;
		}, 3000);
	});
	onDestroy(() => {
		clearInterval(intervalID);
	});
	let nowIndex = 0;
	let topItem = {src: '', href: ''};
	let bottomItem = {src: '', href: ''};

	function TheTimer() {
		if (nowIndex >= imgList.length) nowIndex = 0;
		topItem = imgList.at(nowIndex);
		bottomItem = (nowIndex + 1 >= imgList.length) ? imgList.at(nowIndex + 1 - imgList.length) : imgList.at(nowIndex + 1);
		nowIndex++;
		//console.log(topItem, bottomItem);
	}

</script>

<main>
    <div class="outBox" style="width: {width}px;">
        <div class="inBox" style="right: {-$twYCer}px;">
            <a href="{topItem.href}" class="topA well" style="width: {width}px;">
                <img src="{bottomItem.src}" alt="{bottomItem.src}">
            </a>

            <a href="{bottomItem.href}" class="bottomA well" style="width: {width}px;">
                <img src="{topItem.src}" alt="{topItem.src}">
            </a>
        </div>
    </div>
</main>

<style>
    .outBox {
        border-radius: 10px 10px 0 0;
        -webkit-border-radius: 10px 10px 0 0;
        margin-bottom: 10px;
        position: relative;
        aspect-ratio: 320 / 190;
        overflow: hidden;
        transition: all 500ms;
    }

    .outBox:hover {
        transform: scale(1.03);
        box-shadow: 0 0 25px rgba(33, 33, 33, .5);
    }

    .outBox:active {
        transform: scale(0.97);
        box-shadow: 0 0 7px rgba(33, 33, 33, .8);
    }

    .inBox {
        position: absolute;
        display: flex;
        transition: right;
    }

    .well img {
        width: 100%;
        height: 100%;
        background-size: cover;
        aspect-ratio: 320 / 190;
        object-fit: cover;
    }

    .topA, .bottomA {
        display: block;
        aspect-ratio: 320 / 190;
    }
</style>