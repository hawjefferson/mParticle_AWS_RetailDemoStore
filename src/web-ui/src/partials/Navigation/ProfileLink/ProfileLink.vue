<template>
  <router-link to="/profile" aria-label="support" class="support">Profile</router-link>
</template>

<script>

export default {
  name: 'ProfileLink',
};
</script>

<style>
.support {
  width: 40px;
}

.icon {
  transition: fill 150ms ease-in-out;
}

.support:hover .icon,
.support:focus .icon {
  fill: var(--blue-600);
}
</style>
