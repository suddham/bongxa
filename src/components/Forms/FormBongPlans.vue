<template>
  <div class="text-center">
    <h1 class="text-4xl">Pick a Bong Plan</h1>

    <h2 class="max-w-xl mx-auto py-2 pb-10">
      We travel around the world to source the best bongs for your needs. These bong plans will
      entice you to eternal highs. Select a plan to enter a monthly subscription of bongs from
      around the world based on their quality.
    </h2>

    <div class="plans grid grid-cols-3 gap-4">
      <div
        v-for="plan in plans"
        :key="plan.id"
        @click.prevent="pickPlan(plan)"
        :class="{
          'border-4 border-green-500 rounded-2xl border-opacity-75': selectedPlan === plan,
        }"
        class="plan"
      >
        <FormCard :cardData="plan" @planSelected="pickPlan" />
      </div>
    </div>
    <div v-if="v$.selectedPlan.$error" class="error">You need to pick a plan to continue</div>
  </div>
</template>
<script>
import useVuelidate from '@vuelidate/core';
import { required } from '@vuelidate/validators';
import FormCard from '@/components/UI/FormCard.vue';

export default {
  components: {
    FormCard,
  },
  setup() {
    return { v$: useVuelidate() };
  },
  data() {
    return {
      selectedPlan: null,
      plans: [
        {
          id: 1,
          price: 200,
          weight: '150g',
          title: 'Unidentified Smoking Object',
          description: 'One type of freshly baked glass bong delivered to your house every month',
        },
        {
          id: 2,
          price: 220,
          weight: '200g',
          title: 'LeBong James',
          description:
            'Two types of freshly baked double ceramic glass bongs delivered to your house every month',
        },
        {
          id: 3,
          price: 230,
          weight: '250g',
          title: 'Puff Daddy',
          description:
            'Three types of freshly baked über ceramic glass bongs delivered to your house every month',
        },
        {
          id: 4,
          price: 240,
          weight: '300g',
          title: 'Bong Solo',
          description:
            'Four types of freshly baked steel plated bongs delivered to your house every month',
        },
        {
          id: 5,
          price: 250,
          weight: '350g',
          title: 'Bong Travolta',
          description:
            'Five types of freshly baked silver plated bongs delivered to your house every month',
        },
        {
          id: 6,
          price: 260,
          weight: '400g',
          title: 'Willy Bongka',
          description:
            'Six types of freshly baked gold plated bongs delivered to your house every month',
        },
        {
          id: 7,
          price: 270,
          weight: '450g',
          title: 'Wesley Pipes',
          description:
            'Seven types of freshly baked diamond plated bongs delivered to your house every month',
        },
        {
          id: 8,
          price: 280,
          weight: '500g',
          title: 'Bong Almighty',
          description:
            'Eight types of freshly baked platinum plated bongs delivered to your house every month',
        },
      ],
    };
  },
  validations() {
    return {
      selectedPlan: { required },
    };
  },
  methods: {
    pickPlan(plan) {
      this.selectedPlan = plan;
      this.$emit('userDataProvided', { selectedPlan: plan });
    },
  },
};
</script>

<style lang="scss" scoped></style>
