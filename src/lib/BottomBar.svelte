<script>

	let isTouch = -1;

</script>
<svelte:window on:pointerup={()=>isTouch = -1}/>
<main>
    <div class="bottomBar">
        <a class="iconBox" class:myActive={isTouch===0} on:pointerdown={()=>isTouch=0} href="https://www.musestar.top/">
            <img src="https://www.musestar.top/ms.ico" alt="主页" class="defImgIcon">
            <p class="iconName">首页</p>
        </a>
        <a class="iconBox" class:myActive={isTouch===1} on:pointerdown={()=>isTouch=1} href="https://www.musestar.top/animation">
            <span class="iconfont defIcon">&#xfc2a;</span>
            <p class="iconName">动漫</p>
        </a>
        <a class="iconBox hL" class:myActive={isTouch===2} on:pointerdown={()=>isTouch=2} href="https://www.musestar.top/movie">
            <span class="iconfont defIcon">&#xfc48;</span>
            <p class="iconName">影视</p>
        </a>
        <a class="iconBox" class:myActive={isTouch===3} on:pointerdown={()=>isTouch=3} href="http://www.musestars.top/">
            <span class="iconfont defIcon">&#xfc3a;</span>
            <p class="iconName">搜索</p>
        </a>
        <a class="iconBox" class:myActive={isTouch===4} on:pointerdown={()=>isTouch=4} href="https://www.musestar.top/musestar">
            <span class="iconfont defIcon">&#xfc6b;</span>
            <p class="iconName">官方</p>
        </a>
    </div>
</main>

<style>
    .bottomBar {
        z-index: 9999;
        display: flex;
        align-items: center;
        justify-content: space-around;
        position: fixed;
        bottom: 0;
        width: 100%;
        height: 60px;
        background-color: #333;
        border-top: 2px #555 solid;
        box-shadow: 0 0 7px #333333FF;
    }

    .iconBox {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    .defIcon {
        font-size: 30px;
        color: #ccc;
        transition: color 200ms;
    }

    .iconName {
        font-size: 12px;
        color: #999;
        transition: color 200ms;
    }

    .hL .defIcon {
        color: #2785BD;
    }

    .hL .iconName {
        color: #1C618A;
    }

    .myActive .defIcon {
        color: #3967FF;
    }

    .myActive .iconName {
        color: #ccc;
    }

    .defImgIcon {
        width: 30px;
        transition: all 200ms;
    }

    .myActive .defImgIcon {
        transform: scale(1.2);
    }
</style>