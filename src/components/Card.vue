<template>
  <div class="q-pa-md">
    <div class="row shadow-11">
      <div class="col-md-auto">
        <q-img class="img" height="18rem" width="18rem" :ration="1" :src="user.avatarUrl" />
      </div>
      <div class="col-12 col-md-auto float-left text-weight-bolder">
        <q-img class="banner inset-shadow" width="31rem" height="14rem" :ratio="16/9" :src="user.bannerUrl" />
        <p><q-icon class="fas fa-user" />User ID: <span class="highlight">{{ user.id }}</span></p>
        <p><q-icon class="fas fa-hashtag"/>Username: <span class="highlight">{{ user.name }}</span></p>
        <p v-if="user.bot"><q-icon class="fas fa-robot" />Bot: <span class="highlight">{{ user.bot }}</span></p>
        <p><q-icon class="fas fa-asterisk" />Created: <span class="highlight">{{ user.createdAt }}</span></p>
        <p v-if="user.bannerColor"><q-icon class="fas fa-palette" />Banner color: <span :style="{backgroundColor: user.bannerColor}">{{ user.bannerColor }}</span></p>
      </div>
    </div>
  </div>
</template>

<script>
import {defineComponent} from 'vue';

export default defineComponent({
name: 'Card',
props: {
    user: {
        type: Object,
        required: true
    }
}

})
</script>

<style lang="sass" scoped>
.row > div
  padding: 10px 15px
  background: rgba(0, 0, 0, .15)
  border: 1px solid rgba(86,61,124,.2)
.row + .row
  margin-top: 1rem

.banner  
    width: 31rem
    height: 14rem

.img 
  border-radius: 50%

.highlight 
  color: red
</style>
