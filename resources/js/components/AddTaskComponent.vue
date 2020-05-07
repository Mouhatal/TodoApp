<template>
    <div>
        <!-- Button trigger modal -->
        <button type="button" class="btn btn-primary my-3" data-backdrop="true" data-toggle="modal" data-target="#exampleModal">
        Ajouter une tâche
        </button>

        <!-- Modal -->
        <div class="modal fade" id="exampleModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
            <div class="modal-dialog" role="document">
                <div class="modal-content">
                    <div class="modal-header">
                        <h5 class="modal-title" id="exampleModalLabel">Ajouter une tâche</h5>
                        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                        <span aria-hidden="true">&times;</span>
                        </button>
                    </div>
                    <div class="modal-body">
                        <form action="">
                            <div class="form-group">
                                <label for="task">Nom de la tache</label>
                                <input type="text" name="task" id="task" class="form-control" v-model="name">
                            </div>
                        </form>
                    </div>
                    <div class="modal-footer">
                        <button type="button" class="btn btn-danger" data-dismiss="modal">Annuler</button>
                        <button type="submit" class="btn btn-primary" data-dismiss="modal" @click="addtask">Ajouter</button>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        mounted() {
            console.log('Component mounted.')
        },

        data(){
            return{
                name:''
            }
        },

        methods: {
            addtask(){
                axios.post('http://localhost:8000/taskslist',{
                    name: this.name
                })
                .then(response =>this.$emit('task-added',response))
                .catch(error => console.log(error));
            }
        },

    }
</script>