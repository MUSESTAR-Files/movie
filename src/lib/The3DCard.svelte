<script>
	import {tweened} from 'svelte/motion';
	import {cubicOut} from 'svelte/easing';
	import {onMount,onDestroy} from 'svelte';

	let isOver = false;
	export let backgroundImage = "";
	let theBox;
	let isMouseDown = tweened(0, {
		duration: 300,
		easing: cubicOut
	});
	let isIfC = false;
	const twXCer = tweened(0, {
		duration: 500,
		easing: cubicOut
	});
	const twYCer = tweened(0, {
		duration: 500,
		easing: cubicOut
	});
	const twSize = tweened(0, {
		duration: 500,
		easing: cubicOut
	});

	let cTcRect;
	let theX;
	let theY;
	let theWidth;
	let theHeight;

	function setOXY() {
		if (isOver === true) {
			cTcRect = theBox.getBoundingClientRect();
			theX = cTcRect.x;
			theY = cTcRect.y;
			theWidth = cTcRect.width;
			theHeight = cTcRect.height;
			//console.log('isRun',theX,theY);
		}
	}

	onMount(() => {
		isOver = true;
		setOXY();
	});

	onDestroy(setOXY);

	function setTw(e) {
		if (isIfC) {
			$twXCer = Math.min(Math.max((e.clientX - theX - Math.round(theWidth / 2)) / 5, -45), 45);
			$twYCer = Math.min(Math.max(-(e.clientY - theY - Math.round(theHeight / 2)) / 7, -45), 45);
		}
	}
	function set0() {
		$twXCer = 0;
		$twYCer = 0;
		isIfC = false;
		$isMouseDown = 0;
	}

	function beBig() {
		$twSize = 1.1;
	}

	function beOrg() {
		$twSize = 0;
	}
</script>
<svelte:window on:scroll={setOXY} on:resize={setOXY} on:musemove={setOXY}/>
<main>

    <div
            class="super"
            on:mouseenter={beBig}
            on:mousemove={setTw}
            on:mousedown={(e)=>{$isMouseDown=60;isIfC=true;setTw(e)}}
            on:mouseup={()=>{$isMouseDown=0;isIfC=false;set0()}}
            on:mouseleave={(e)=>{set0(e);beOrg()}}
    >
        <div
                bind:this={theBox}
                class="mBox"
                style="background-image: url({backgroundImage});transform: translateZ({-$isMouseDown+($twSize*25)}px) rotateX({$twYCer}deg) rotateY({$twXCer}deg);"
        >
            <slot></slot>
        </div>
    </div>

</main>
<style>
    .super {
        user-select: none !important;
        perspective: 800px;
        display: inline-block;
    }

    .mBox {
        overflow: hidden;
        height: 280px;
        width: 190px;
        background-color: deepskyblue;
        border-radius: 10px;
        background-repeat: no-repeat;
        background-size: cover;
    }


</style>