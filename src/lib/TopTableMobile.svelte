<script>
	import ScroImgMobile from './ScroImgMobile.svelte';
    export let imgList = [
        {src: '图片', href: 'https://www.musestar.top/'}
    ]
	export let width = 320;
</script>

<main>

    <div class="forImg">
        <div class="overHid">
            <ScroImgMobile width="{width}" {imgList}/>
        </div>
    </div>

</main>

<style>
    .forImg {
        display: flex;
        justify-content: center;
    }
    .overHid{
        border-radius: 10px 10px 0 0;
        -webkit-border-radius: 10px 10px 0 0;
        overflow: hidden;
    }
</style>