<!-- eslint-disable vue/require-v-for-key -->
<template>
    <div class="users">
        <div class="nom">
            <label for="nom">Nom :</label>
            <input type="text" placeholder="NOM">
        </div>
        <div class="prenom">
            <label for="prenom">Prénom:</label>
            <input type="text" placeholder="Prénom">
        </div>
        <div class="email">
            <label for="email">Email:</label>
            <input type="email" name="email" id="email" placeholder="email@mail.com">
        </div>
        <button>S'inscrire</button>
    </div>
    <div class="user"  >
        <p v-for="user of users" :key="user.nom">{{ user.nom }}  {{ user.prenom }}</p>

    </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Inscription-user',
  components:{
  },
  data(){
    return{
        users : []
    }
    
  },

  async created(){
    try{
        const res = await axios.get("http://localhost:3000/users");
        this.users = res.data;
        console.log(this.users)
    }catch(error){
        console.log(error);
    }
  }

  }
</script>

<style>
</style>