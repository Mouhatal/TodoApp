<template>
    <div>
        <!-- Modal -->
        <div class="modal fade" id="editModal" tabindex="-1" role="dialog" aria-labelledby="editModalLabel" aria-hidden="true">
            <div class="modal-dialog" role="document">
                <div class="modal-content">
                    <div class="modal-header">
                        <h5 class="modal-title" id="editModalLabel">Modifier la tâche</h5>
                        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                        <span aria-hidden="true">&times;</span>
                        </button>
                    </div>
                    <div class="modal-body">
                        <form action="">
                            <div class="form-group">
                                <label for="task">Nom de la tache</label>
                                <input type="text" name="task" id="task" class="form-control" v-model="taskToEdit.name">
                            </div>
                        </form>
                    </div>
                    <div class="modal-footer">
                        <button type="button" class="btn btn-danger" data-dismiss="modal">Annuler</button>
                        <button type="submit" class="btn btn-primary" data-dismiss="modal" @click="update">Enregistrer</button>
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

        props:['taskToEdit'],

        methods:{
            update(){
                axios.patch('http://localhost:8000/tasks/edit/'+this.taskToEdit.id,{
                    name: this.taskToEdit.name
                })
                    .then(response=>this.$emit('task-updated',response))
                    .catch(error=>console.log(error));
            }
        }

    }
</script>