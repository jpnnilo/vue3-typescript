<template>
 

        <v-app>
            <v-main>
                <v-container>
                    
              
               
                    <h1>Animals List</h1>
                    <v-table>
                        <thead>
                        <tr>
                            <th class="text-left">Name</th>
                            <th class="text-center">
                            Breed
                            </th> 
                            <th class="text-center">
                            Gender
                            </th>
                            <th class="text-center">
                            Age
                            </th>
                            <th class="text-center">
                            Type
                            </th>
                            <th class="text-center">
                            Action
                            </th>
                        </tr>
                        </thead>
                        <tbody>
                        <tr
                            v-for="animal in animals"
                            :key="animal"
                        >
                            <td class="text-left"   >{{ animal.name }}</td>
                            <td>{{ animal.breed }}</td>
                            <td>{{ animal.age }}</td>
                            <td>{{ animal.gender }}</td>
                            <td>{{ animal.type }}</td>
                        </tr>
                        </tbody>
                    </v-table>
                </v-container>
            </v-main>
        </v-app>
    
</template>

<script setup lang="ts">
import { ref, onMounted} from 'vue';
import axios from 'axios'


let animals = ref([]);

viewAnimals()

function viewAnimals(){
    axios.get(`http://127.0.0.1:8000/api/animal`)
    .then((success) => {console.log(success.data.animals)
        animals.value = success.data.animals;
    })
    .catch((error)=> {console.log(error)}) 
}

onMounted(() => {
   console.log('test');

   
})


</script>


<style scoped>


</style>