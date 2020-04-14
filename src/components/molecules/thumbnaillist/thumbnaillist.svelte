<script>
    import Descriptiontext from '../../atoms/descriptiontext/description.svelte'; 
    import Image from '../../atoms/image/image.svelte'; 
    export let items;
    export let baseUrl;
</script>

<style>
    li{
        list-style:none;
    }
    figure{
        margin:0;
        padding:0;
    }
</style>
<li>
    <figure>
        <Image items={items} baseUrl={baseUrl} />
        <Descriptiontext items={items} />        
    </figure>
</li>
