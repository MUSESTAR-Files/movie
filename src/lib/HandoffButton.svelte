<script>
    let theS = true;//真为番剧，假为剧场
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();
    $:dispatch(`theChn`, theS)
</script>

<main>
    <div class="mainBox">
        <button class="oneBtn fistBtn" class:isS={theS} on:click={()=>{theS=true}}>电影</button>
        <button class="oneBtn lastBtn" class:isS={!theS} on:click={()=>{theS=false}}>剧集</button>
    </div>
</main>

<style>
.mainBox{
    z-index: 99;
    height: 98px;
    width: 28px;
    background-color: transparent;
    display: flex;
    flex-direction: column;
    position: fixed;
    top: 310px;
    border: #333333CC 2px solid;
    border-radius: 0 10px 10px 0;
    overflow: hidden;
}
.oneBtn{
    border: 0;
    padding: 0;
    margin: 0;
    height: 50%;
    width: 100%;
    background-color: #33333399;
    -webkit-backdrop-filter: blur(5px);
    backdrop-filter: blur(5px);
    color: #FFFFFFCC;
    transition: all 250ms;
}
.fistBtn{
    border-bottom: #33333344 1px solid;
}
.lastBtn{
    border-top: #33333344 1px solid;
}
.isS{
    background-color: #2785BDCC;
    color: white;
}
</style>