<template>
  <div class="profile-card">
    <p class="text-center">
      <img
        :src="userStore.authUser.avatar"
        :alt="`${userStore.name} profile picture`"
        class="avatar-xlarge img-update"
      />
    </p>

    <div class="form-group">
      <input
        v-model="activeUser.username"
        type="text"
        placeholder="Username"
        class="form-input text-lead text-bold"
      />
    </div>

    <div class="form-group">
      <input
        v-model="activeUser.name"
        type="text"
        placeholder="Full Name"
        class="form-input text-lead"
      />
    </div>

    <div class="form-group">
      <label for="user_bio">Bio</label>
      <textarea
        v-model="activeUser.bio"
        class="form-input"
        id="user_bio"
        placeholder="Write a few words about yourself."
      ></textarea>
    </div>

    <div class="stats">
      <span>{{ userPostsCount }} posts</span>
      <span>{{ userThreadsCount }} threads</span>
    </div>

    <hr />

    <div class="form-group">
      <label class="form-label" for="user_website">Website</label>
      <input v-model="activeUser.website" autocomplete="off" class="form-input" id="user_website" />
    </div>

    <div class="form-group">
      <label class="form-label" for="user_email">Email</label>
      <input v-model="activeUser.email" autocomplete="off" class="form-input" id="user_email" />
    </div>

    <div class="form-group">
      <label class="form-label" for="user_location">Location</label>
      <input v-model="activeUser.location" autocomplete="off" class="form-input" id="user_location" />
    </div>

    <div class="btn-group space-between">
      <button class="btn-ghost">Cancel</button>
      <button type="submit" class="btn-blue">Save</button>
    </div>
  </div>
</template>

<script setup>
import { useUserStore } from '@/stores/UserStore'
import { computed } from 'vue'
const userStore = useUserStore()
const userPostsCount = computed(() => userStore.userPosts.length)
const userThreadsCount = computed(() => userStore.userThreads.length)

const activeUser = { ...userStore.authUser }
</script>
