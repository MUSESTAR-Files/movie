<script>
	import MovCardMobile from './lib/MovCardMobile.svelte';
	import TopBar from './lib/TopBar.svelte';
	import BottomBar from './lib/BottomBar.svelte';
	import MovCard from './lib/MovCard.svelte';
	import TopTable from './lib/TopTable.svelte';
	import HandoffBar from './lib/HandoffBar.svelte';
	import PcUnder from './lib/PcUnder.svelte';
	import TopTableMobile from './lib/TopTableMobile.svelte';
	import HandoffButton from './lib/HandoffButton.svelte';
	import MobileUnder from './lib/MobileUnder.svelte';

	import {blur} from 'svelte/transition';
	import {TheBangumiList, TheBangumiMoveList, TheImgList} from './js/BangumiList';
	import {onMount} from 'svelte';

	let theS = true;//真为番剧，假为剧场
    let isBgLoaded = false;

	const bangumiList = TheBangumiList();
	const bangumiMoveList = TheBangumiMoveList();
    const imgList = TheImgList();

	const isMobile = /Android|webOS|iPhone|iPod|BlackBerry/i.test(navigator.userAgent);
	let bodyWidth = document.body.clientWidth;
	onMount(() => {
		bodyWidth = document.body.clientWidth;
	});
</script>
<main>
    <img src="{isMobile?'https://t.alcy.cc/pc/':'https://t.alcy.cc/pc/'}" class="backG"
         alt="back" loading="eager" on:loadstart={()=>{isBgLoaded = false}} on:load={()=>{isBgLoaded = true}} class:noDisplay={!isBgLoaded}>
    {#if isMobile}
        <HandoffButton on:theChn={(e)=>{theS=e.detail;}}/>
        <BottomBar/>
        <div class="onBG">
            <div class="mainBox mpMainBox">
                <div class="mpCardBox">
                    <TopTableMobile width="{bodyWidth * .85}" {imgList}/>
                    <div class="mBoxMobile">
                        {#if theS}
                            {#each bangumiList as item}
                                <div class="cardBoxMobile"
                                     in:blur={{duration:190,delay:170,opacity:0.2,amount: 15}}
                                     out:blur={{duration:190,opacity:0.3,amount: 5}}>
                                    <MovCardMobile theBangumi="{item}"/>
                                </div>
                            {/each}
                        {:else}
                            {#each bangumiMoveList as item}
                                <div class="cardBoxMobile"
                                     in:blur={{duration:190,delay:170,opacity:0.2,amount: 15}}
                                     out:blur={{duration:190,opacity:0.3,amount: 5}}>
                                    <MovCardMobile theBangumi="{item}"/>
                                </div>
                            {/each}
                        {/if}
                        <!--下面这些是为了自适应的填充物-->
                        <i class="paddingIn"></i>
                        <i class="paddingIn"></i>
                        <i class="paddingIn"></i>
                        <i class="paddingIn"></i>
                        <i class="paddingIn"></i>
                        <i class="paddingIn"></i>
                        <i class="paddingIn"></i>
                        <i class="paddingIn"></i>
                        <i class="paddingIn"></i>
                        <i class="paddingIn"></i>
                        <i class="paddingIn"></i>
                        <i class="paddingIn"></i>
                        <i class="paddingIn"></i>
                        <i class="paddingIn"></i>
                        <i class="paddingIn"></i>
                        <i class="paddingIn"></i>
                        <i class="paddingIn"></i>
                        <i class="paddingIn"></i>
                        <i class="paddingIn"></i>
                        <i class="paddingIn"></i>
                    </div>
                </div>
            </div>
        </div>
        <div style="text-align: center; background-size: cover;">
            <img width=350 src="https://moe-counter.yumetsuki.moe/get/@musestar?theme=rule34" alt="musestar">
        </div>
        <MobileUnder/>
    {:else}
        <TopBar/>
        <div class="mainBox pcMainBox">
            <TopTable {imgList}/>
            <div class="blurBox">
                <HandoffBar on:theChn={(e)=>{theS=e.detail;}}/>
                <div class="cardBox">
                    {#if theS}
                        {#each bangumiList as item}
                            <div class="mCard"
                                 in:blur={{duration:250,delay:200,opacity:0.2,amount: 15}}
                                 out:blur={{duration:250,opacity:0.3,amount: 15}}
                            >
                                <MovCard theBangumi={item}/>
                            </div>
                        {/each}
                    {:else}
                        {#each bangumiMoveList as item}
                            <div class="mCard"
                                 in:blur={{duration:250,delay:200,opacity:0.2,amount: 15}}
                                 out:blur={{duration:250,opacity:0.3,amount: 15}}
                            >
                                <MovCard theBangumi={item}/>
                            </div>
                        {/each}
                    {/if}
                    <!--下面这些是为了自适应的填充物-->
                    <i class="paddingIn"></i>
                    <i class="paddingIn"></i>
                    <i class="paddingIn"></i>
                    <i class="paddingIn"></i>
                    <i class="paddingIn"></i>
                    <i class="paddingIn"></i>
                    <i class="paddingIn"></i>
                    <i class="paddingIn"></i>
                    <i class="paddingIn"></i>
                    <i class="paddingIn"></i>
                    <i class="paddingIn"></i>
                    <i class="paddingIn"></i>
                    <i class="paddingIn"></i>
                    <i class="paddingIn"></i>
                    <i class="paddingIn"></i>
                    <i class="paddingIn"></i>
                    <i class="paddingIn"></i>
                    <i class="paddingIn"></i>
                    <i class="paddingIn"></i>
                    <i class="paddingIn"></i>
                </div>
            </div>
        </div>
        <div style="text-align: center; background-size: cover;">
            <img width=350 src="https://moe-counter.yumetsuki.moe/get/@musestar?theme=rule34" alt="musestar">
        </div>
        <div class="pcUnder">
            <PcUnder/>
        </div>
    {/if}

</main>

<style>
    .backG {
        position: fixed;
        top: 0;
        left: 0;
        z-index: -2;
        width: 100%;
        height: 100%;
        object-fit: cover;
    }

    .mpMainBox {
        width: 100%;
        padding: 0;
    }

    .pcMainBox {
        min-width: 730px;
        margin: 100px 15vw 60px 15vw;
        border-radius: 7px;
        overflow: hidden;
    }

    .blurBox {
        width: 100%;
        height: 100%;
        backdrop-filter: blur(10px);
        background-color: rgba(66, 66, 66, .7);
        padding: 0;
    }

    .cardBox {
        margin-top: 18px;
        display: flex;
        flex-wrap: wrap;
        justify-content: space-around;
    }

    .cardBox .mCard {
        margin: 0 25px 25px;
    }

    .paddingIn {
        width: 190px;
        margin: 0 25px;
    }

    .pcUnder {
        position: relative;
        bottom: 0;
    }

    .mpCardBox {
        margin: 0;
    }

    .onBG {
        padding: 0;
        z-index: -1;
        display: flex;
        width: 85%;
        backdrop-filter: blur(5px);
        -webkit-backdrop-filter: blur(5px);
        background-color: rgba(66, 66, 66, .7);

        border-radius: 10px;
        overflow: hidden;

        box-shadow: 0 0 12px rgba(133,133,133.8);
        margin: 50px auto 25px;
    }

    :global(body) {
        background-color: rgb(66, 66, 66);
    }

    .mBoxMobile {
        margin-top: 30px;
        display: flex;
        justify-content: space-around;
        flex-wrap: wrap;
        padding: 0 15px 25px;
    }

    .mBoxMobile > .paddingIn {
        width: 130px;
        margin: 0;
    }

    .cardBoxMobile {
        margin: 0 7px 7px;
    }

    .noDisplay{
        display: none !important;
    }
</style>
