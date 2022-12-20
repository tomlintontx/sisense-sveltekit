<script lang="ts">
    import Svelecte from 'svelecte'

    let options = [{id:'years', name: 'years'},{id:'quarters', name: 'quarters'},{id:'months', name: 'months'},{id:'days', name: 'days'},];

    let message= {
        sender: 'sisense',
        type: 'gran',
        value: ''
    };

    let postMessage = (target:Element) => {
        target.contentWindow.postMessage(message,'*');
    }

    let changeGran = function () {

        console.log(message)

        let targetWindow = document.getElementById('sisense-frame')!

        postMessage(targetWindow)

    }

</script>


<div id="sisenseApp">
    <div id='toolbar'>
        <div id="selector-cont">
            <Svelecte options={options} bind:value={message.value} placeholder="Choose an option..."></Svelecte>
        </div>
        <button id="gran-changer" on:click={changeGran}>Submit</button>
    </div>
    <iframe src='https://tams.sisensepoc.com/app/main/dashboards/6310e91b131c34002be63418' id="sisense-frame" width="100%" height="100%" title="sisense" frameborder=none></iframe>
</div>



<style>

#sisenseApp {
    height: 100%;
    width: 100%;
}

#toolbar {
    width: 100%;
    background-color: dodgerblue;
    height: 3rem;
    display:flex;
    align-items: center;
}

#selector-cont {
    width: 30%;
    margin-left: 1rem;
}

#gran-changer {
    margin-left: 1rem;
    height: 2rem;
}

</style>