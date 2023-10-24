<script>
    import ToDoControls from './ToDoControls.svelte';
    import ToDoItem from './ToDoItem.svelte';
    let items=[
        {
            id:1,
            text:'some',
            isDone: true 
        } ,    
        {
            id:2,
            text:'asasas',
            isDone: false
        }
    ];
    function onChangeStatus(event){
       
        const item= items.find((i) =>i.id ===event.detail.id);
        item.isDone=!item.isDone;
        items=items;
    }
</script>


<div class="todo-app">
    <ToDoControls/>
    <div class="todo-app__field">
        {#each items as item }
            <ToDoItem id={item.id} text={item.text} isDone={item.isDone} on:change={onChangeStatus} />
        {/each}
        
    </div>
</div>

<style> 
    .todo-app{
        width: 700px;
        height:80%;
        background: gray;
        border-radius: 15px;
        padding: 40px;
        display: flex;
        flex-direction: column;
        gap:30px;
    }
    .todo-app__field{
        background: white;
        flex-grow: 1;
        border-radius: 15px;
        overflow-y: auto;
        padding: 20px; 
        display: flex;
        flex-direction: column;
        gap:20px
    }
</style>

