<template>
  <div>
    <div class="card lg:card-side bordered">
      <div class="card shadow-lg compact side bg-base-100">
        <div class="flex-row items-center space-x-4 card-body text-left">
          <div class="flex-1">
            <h2 class="card-title">{{ cardData.title }}</h2>
            <p class="text-base-content text-opacity-40">{{ cardData.description }}</p>
            <span class="text-xl"> {{ cardData.weight }}</span> for

            <span class="text-3xl"> $ </span>
            <span class="text-2xl"> {{ cardData.price }}</span>
          </div>
          <div class="flex-0">
            <button class="btn btn-sm" @click="() => $emit('planSelected')">Select Plan</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    cardData: {
      type: Object,
      required: false,
      default: () => {},
    },
  },
};
</script>
