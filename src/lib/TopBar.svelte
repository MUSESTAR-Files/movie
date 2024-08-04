<script>
	const isMobile = false;
</script>

<main>

    <div class="THeTopBar" class:TheTopBarPC={!isMobile} class:TheTopBarMo={isMobile}>
        <a class="oneBlock" href="/">
            <img src=/favicon.ico alt="Musestar" class="msIcon">
        </a>
        <div class="inTopA inTopFirst hgLtBox">
            <a href="/movie" class="hgLt">缪斯星影视</a>
        </div>
        <div class="inTopA">
            <a href="/animation">缪斯星动漫</a>
        </div>
        <div class="inTopA">
            <a href="http://search.musestar.cc/">缪斯星搜索</a>
        </div>
        <div class="inTopA inTopLast">
            <a href="/musestar">缪斯星官方</a>
        </div>

    </div>
</main>

<style>

    .hgLt {
        color: #2785BDDD !important;
        position: relative;
        font-size: 22px !important;
        font-family: SmileySans;
    }
    .inTopFirst{
        border-right: 0 !important;
        background-color: transparent !important;
        margin: 0 auto;
    }
    .hgLt:before{
        content: '';
        border-radius: 2px;
        width: 36px;
        height: 3px;
        background-color: #2785BD;
        position: absolute;
        bottom: -19px;
        right: calc(50% - 18px);
    }
    .THeTopBar {
        position: fixed;
        top: 0;
        background-color: #333333DD;
        backdrop-filter: blur(10px);
        display: flex;
        align-items: center;
        perspective: 800px;
        z-index: 9999;
    }

    .TheTopBarPC {
        width: 100%;
        height: 60px;
        min-width: 910px;
        padding: 0 15vw;
    }

    .TheTopBarMo {
        width: 100%;
        height: 4vh;
        min-height: 40px;
        min-width: 710px;
    }

    .THeTopBar > .inTopLast {
        border-right: 0;
    }

    .inTopA:hover {
        background-color: #555555DD;

    }

    .inTopA:hover > a {
        color: #ccccccDD;
    }

    .inTopA:active {
        background-color: #2785BD;
    }

    .inTopA:active > a {
        color: #ffffffDD;
    }

    .inTopA {
        padding: 0 25px;
        height: 100%;
        display: flex;
        align-items: center;
        transition: background-color 300ms;
        border-right: #555 1px solid;
    }

    .inTopA > a {
        display: inline-block;
        color: #ccc;
        text-decoration: none;
        font-size: 14px;
        line-height: 100%;
        text-align: center;
        transition: color 500ms;
        font-family: SmileySans;
    }

    .msIcon {
        line-height: 100%;
        height: 70%;
    }

    .oneBlock:link {
        animation-name: reTeShadow;
        animation-duration: 500ms;
        animation-fill-mode: forwards;
        margin-right: auto;
        height: 100%;
        aspect-ratio: 1/1;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .oneBlock:hover {
        animation-name: teShadow;
        animation-duration: 500ms;
        animation-fill-mode: forwards;
    }

    .oneBlock:active {
        animation-name: reTeShadow;
        animation-duration: 300ms;
        animation-fill-mode: forwards;
    }

    @keyframes teShadow {
        from {
            filter: drop-shadow(0 0 10px rgba(46, 159, 227, .0));
            transform: scale(1);
        }

        to {
            filter: drop-shadow(0 0 10px #b68efb);
            transform: scale(1.2);
        }
    }

    @keyframes reTeShadow {
        from {
            filter: drop-shadow(0 0 10px #b68efb);
            transform: scale(1.2);
        }

        to {
            filter: drop-shadow(0 0 10px rgba(46, 159, 227, .0));
            transform: scale(1);
        }
    }

    .TheTopBarMo > .oneBlock {
        margin-right: 0;
    }

    .TheTopBarMo a {
        font-size: 14px;
    }

    .TheTopBarMo > .inTopA {
        padding: 0 7px;
    }

    .hgLtBox{
        position: absolute;
        right: calc(50% - 75px);
    }
</style>