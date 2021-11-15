<template>
  <div>
    <!-- Actions  -->
    <div>
      <button class="btn btn-primary mx-2" @click="goBack">&#9754; Back</button>
      <button class="btn btn-primary mx-2" @click="goNext">Next &#9755;</button>
    </div>

    <!-- Progress Bar -->
    <div class="progress-bar max-w-2xl mx-auto text-center">
      <div class="p-6 space-y-2">
        <progress class="progress progress-primary" :value="progress" max="100"></progress>
      </div>
    </div>

    <!-- Forms  -->
    <FormBongPlans v-if="currentStepNumber === 1" @userDataProvided="updateUserPayload" />

    <pre><code>{{formPayload}}</code></pre>
  </div>
</template>
<script>
import FormBongPlans from '@/components/Forms/FormBongPlans.vue';

export default {
  name: 'FormWizard',
  components: {
    FormBongPlans,
  },
  data() {
    return {
      currentStepNumber: 1,
      length: 4,
      formPayload: {
        selectedPlan: null,
      },
    };
  },
  computed: {
    progress() {
      return (this.currentStepNumber / this.length) * 100;
    },
  },
  methods: {
    goBack() {
      this.currentStepNumber -= 1;
    },
    goNext() {
      this.currentStepNumber += 1;
    },
    updateUserPayload(payload) {
      Object.keys(payload).forEach((key) => {
        this.formPayload[key] = payload[key];
      });
    },
  },
};
</script>
<style></style>
