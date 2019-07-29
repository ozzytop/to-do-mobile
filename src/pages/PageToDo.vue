<template>
  <q-page class="q-pa-md">
    <q-list bordered >

        <q-item 
            v-for="task in tasks"
            :key="task.id"
            @click="task.completed = !task.completed"
            clickable
            v-ripple>
            <q-item-section side top>
                <q-checkbox v-model="task.completed" />
            </q-item-section>
            <q-item-section>
                <q-item-label>{{task.name}}</q-item-label>
            </q-item-section>
        </q-item>

    </q-list>
  </q-page>
</template>

<style>
</style>

<script>
    export default {
        data(){
            return {
                tasks:[
                    {
                        id: 1,
                        name: 'Go to Shop',
                        completed: false
                    },
                    {
                        id: 2,
                        name: 'Get appels',
                        completed: true
                    },
                    {
                        id: 3,
                        name: 'Go to the cinema',
                        completed: false
                    }
                ]
            }
        }
    };
</script>
