<script>
	import ScroImg from './ScroImg.svelte';

    export let imgList = [
        {src: '图片', href: 'https://www.musestar.cc/'}
    ]
</script>

<main>
    <div class="outBox">
        <img class="pImg" src="https://s1.imagehub.cc/images/2023/01/07/1df6afb9e441c96f03f9eb6e08bdee01.png" alt="anisphere">
        <div class="forImg">
            <ScroImg {imgList}/>
        </div>
        <img class="pImg" src="https://s1.imagehub.cc/images/2023/01/07/c338f0618a89c7260cc42d6c07b1162f.png" alt="euphilia">
    </div>
</main>

<style>
    .forImg {
        margin: 30px;
    }

    .outBox {
        width: 100%;
        display: flex;
        justify-content: space-around;
        background-color: rgba(66, 66, 66, .3);
        backdrop-filter: blur(5px);
        border-bottom: 2px rgba(222,222,222,.7) solid;
    }

    .pImg{
        padding: 25px 25px 0;
        filter: drop-shadow(0 0 10px rgba(33,33,33,.7));
        height: 340px;
    }

    @media screen and (max-width: 1450px){
        .pImg{
            display: none;
        }
    }
</style>