<template>
  <div id="app" class="min-h-screen w-screen
  bg-gray-200 flex items-center justify-center">
    <Draggable tag="ul" ghost-class="moving-card" filter=".action-button" class="w-full max-w-md" :list="users" :animation="200">
      <li 
        v-for="user in users" 
        :key="user.id"
        class="p-4 mb-3 flex justify-between items-center bg-white shadow rounded-lg cursor-move" 
      >
      <div class="flex items-center w-full">
        <img :src="user.avatar" :alt="user.name" class="w-10 h-10 rounded-full">
        <p class="ml-2 text-gray-700 font-semibold tracking-wide">
          {{ user.name }}
        </p>
        <div class="flex ml-auto">
          <button
            aria-label="Edit user"
            class="p-1 focus:outline-none focus:shadow-outline text-green-500 hover:text-green-600"
            @click="onEdit(user)"
          >
            <EditIcon />
          </button>
          <button
            aria-label="Delete user"
            class="p-1 focus:outline-none focus:shadow-outline text-red-500 hover:text-red-600"
            @click="onDelete(user)"
          >
            <Trash2Icon />
          </button>
        </div>
      </div>
      </li>  
    </Draggable>
  </div>
</template>

<script>
import { EditIcon, Trash2Icon } from "vue-feather-icons";
import Draggable from 'vuedraggable';

export default {
  name: 'App',
  data() {
    return {
      users: [
        {
          id: 1,
          name: "Adrian Schubert",
          avatar: "https://pickaface.net/gallery/avatar/unr_sample_161118_2054_ynlrg.png"
        },
        {
          id: 2,
          name: "Violet Gates",
          avatar: "https://pickaface.net/gallery/avatar/freud51c8b3f65e7dc.png"
        },
        {
          id: 3,
          name: "Steve Jobs",
          avatar: "https://pickaface.net/gallery/avatar/Opi51c74d0125fd4.png"
        },
        {
          id: 4,
          name: "Yassine Smith",
          avatar: "https://pickaface.net/gallery/avatar/unr_yassine_191124_2012_3gngr.png"
        },
        {
          id: 5,
          name: "Senior Saez",
          avatar: "https://pickaface.net/gallery/avatar/elmedinilla541c03412955c.png"
        }
      ]
    }
  },
  components: {
    EditIcon,
    Trash2Icon,
    Draggable,
  },

  methods: {
    onEdit(user) {
      console.log(`Editing ${user.name}`);
    },
    onDelete(user) {
      console.log(`Deleting ${user.name}`);
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.moving-card {
  @apply opacity-50 bg-gray-100 border border-blue-500;
}
</style>
