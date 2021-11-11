<template>
  <div>
    <h1>Pick a Bong Plan</h1>

    <h2>
      We travel around the world to source the best bongs for your needs. These bong plans will
      entice you to eternal "nirvanic-highs". Select a plan to enter a monthly subscription of bongs
      from around the world based on their quality.
    </h2>

    <div class="plans">
      <div
        v-for="plan in plans"
        :key="plan.id"
        @click.prevent="pickPlan(plan)"
        :class="{ 'active-plan': selectedPlan === plan }"
        class="plan"
      >
        <div class="weight">{{ plan.weight }}</div>
        <div class="description">
          <span class="title">{{ plan.name }}</span>
        </div>
        <div class="description">
          {{ plan.description }}
        </div>
        <div class="price">
          <span class="dollar-sign">$</span>
          <span class="number">{{ plan.price }}</span>
        </div>
      </div>
    </div>
    <div v-if="v$.selectedPlan.$error" class="error">You need to pick a plan to continue</div>
  </div>
</template>
<script>
import useVuelidate from '@vuelidate/core';
import { required } from '@vuelidate/validators';

export default {
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
          name: 'Unidentified Smoking Object',
          description: 'One type of freshly baked glass bong delivered to your house every month',
        },
        {
          id: 2,
          price: 220,
          weight: '200g',
          name: 'LeBong James',
          description:
            'Two types of freshly baked double ceramic glass bongs delivered to your house every month',
        },
        {
          id: 3,
          price: 230,
          weight: '250g',
          name: 'Puff Daddy',
          description:
            'Three types of freshly baked über ceramic glass bongs delivered to your house every month',
        },
        {
          id: 4,
          price: 240,
          weight: '300g',
          name: 'Bong Solo',
          description:
            'Four types of freshly baked steel plated bongs delivered to your house every month',
        },
        {
          id: 5,
          price: 250,
          weight: '350g',
          name: 'Bong Travolta',
          description:
            'Five types of freshly baked silver plated bongs delivered to your house every month',
        },
        {
          id: 6,
          price: 260,
          weight: '400g',
          name: 'Willy Bongka',
          description:
            'Six types of freshly baked gold plated bongs delivered to your house every month',
        },
        {
          id: 7,
          price: 270,
          weight: '450g',
          name: 'Wesley Pipes',
          description:
            'Seven types of freshly baked diamond plated bongs delivered to your house every month',
        },
        {
          id: 8,
          price: 280,
          weight: '500g',
          name: 'Bong Almighty',
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
    },
  },
};
</script>

<style lang="scss" scoped></style>
