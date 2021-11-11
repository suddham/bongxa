<template>
  <div>
    <!-- Actions  -->
    <div>
      <button class="btn btn-primary">&#9754; Back</button>
      <button class="btn btn-primary">Next &#9755;</button>
    </div>

    <!-- Progress Bar -->
    <div class="progress-bar">
      <div :style="`width: ${progress}%;`"></div>
    </div>

    <!-- Forms  -->
    <FormBongPlans v-if="currentStepNumber === 1" />

    <pre><code>{{form}}</code></pre>
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
      form: {
        selectedBong: null,
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
  },
};
</script>
<style></style>
