<template>
  <q-page class="flex flex-center">
    <div class="flex column flex-right q-pa-sm">
      <UserInput @submit="getUser">Look this dude up!</UserInput>
      <Card v-if="user.id" :user="user"></Card>
    </div>
  </q-page>
</template>

<script>
import { defineComponent, ref } from 'vue';
import { date } from 'quasar'
import { api } from 'boot/axios';
import Card  from 'components/Card.vue'
import UserInput from 'components/UserInput.vue'

export default defineComponent({
  name: 'PageIndex',
  components: {
    Card,
    UserInput
  },

  setup() {
    const user = ref({id: null});
    const getUser = async (id) => {
      await api.get('api/' + id)
        .then((request) => {
          if (request.data.avatar)
            user.value.avatarUrl = `https://cdn.discordapp.com/avatars/${request.data.id}/${request.data.avatar}.png?size=1024`
          if (request.data.banner)
            user.value.bannerUrl = `https://cdn.discordapp.com/banners/${request.data.id}/${request.data.banner}.png?size=1024`
          
          user.value.bannerColor = request.data.banner_color;
          user.value.id = request.data.id;
          user.value.name = `${request.data.username}#${request.data.discriminator}`;
          user.value.createdAt = date.formatDate(convertToUnix(request.data.id), 'dddd, DD MMMM YYYY HH:mm:ss');
          user.value.bot = request.data.bot

          console.log(user.value)
        })
    }
    return {getUser, user}
  }
})
function convertToUnix(id) {
  let bin = (+id).toString(2);

  let unixbin = '';
  let unix = '';
  
  let m = 64 - bin.length;
  unixbin = bin.substring(0, 42-m);
  unix = parseInt(unixbin, 2) + 1420070400000;

  return unix;
}
</script>
