<script>
	import {onMount, onDestroy} from 'svelte';

	const startTime = (new Date(2022, 4, 25)).getTime();
	let sense = '';
	let idInterval;
	onMount(() => {
		idInterval = setInterval(() => {
			sense = formatDuring((new Date()).getTime() - startTime);
		}, 500);
	});
	onDestroy(() => {
		clearInterval(idInterval);
	});

	function formatDuring(mss) {
		const days = Math.floor(mss / (1000 * 60 * 60 * 24));
		const hours = Math.floor((mss % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
		const minutes = Math.floor((mss % (1000 * 60 * 60)) / (1000 * 60));
		const seconds = ((mss % (1000 * 60)) / 1000).toFixed(0);
		return days + " 天 " + hours + " 小时 " + minutes + " 分钟 " + seconds + " 秒 ";
	}


</script>

<main>
    <div class="mainBox">
        <a href="/" class="webMap"><span>&copy; 2025 MUSESTAR</span></a>
        <a href="https://icp.gov.moe/?keyword=20226956" class="webMap"><span>萌ICP备20226956号</span></a>
        <a href="https://stats.uptimerobot.com/NJ9gBiMZ7D" class="webMap"><span>缪斯星服务状态</span></a>
        <i class="time">本站已运行 {sense}</i>
    </div>
</main>

<style>
    .mainBox {
        width: 100%;
        height: 195px;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        background-color: #333333DD;
        backdrop-filter: blur(10px);
        color: white;
    }

    .grText {
        font-size: 15px;
        color: #aaa;
    }

    .time {
        font-size: 15px;
        color: #aaa;
        padding-top: 15px;
        font-style: normal;
    }

    .webMap:link {
        font-size: 15px;
        color: #aaa;
    }

    .webMap:visited {
        color: #aaa;
    }

    .webMap:hover {
        color: #1C618A;
    }

    .webMap:active {
        color: #2785BD;
    }
</style>