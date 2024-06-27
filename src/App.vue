<template>
  <div :class="[{ isReady }]">
    <button @click="shouldFetch = !shouldFetch">toggle expand</button>
    <template v-for="(value, i) in ['foo']" :key="value">
      <OtherComponent>
        <div :data-i="i">
          <OtherComponent>
            <div>
              <div>
                <template v-if="shouldFetch">open</template>
                <template v-else>closed</template>
              </div>
            </div>
            <template v-if="shouldFetch">open</template>
            <div v-else></div>
          </OtherComponent>
        </div>
      </OtherComponent>
    </template>
  </div>
</template>

<script setup>
import { ref, watch, computed } from 'vue'
import OtherComponent from './OtherComponent.vue'

const shouldFetch = ref(false)
const hasLoaded = ref(false)
const isReady = computed(() => shouldFetch.value && hasLoaded.value)

const fetchData = async () => new Promise(resolve => setTimeout(() => resolve(), 100))

watch(shouldFetch, shouldFetch => {
  if (shouldFetch) {
    hasLoaded.value = false
    fetchData().then(() => {
      hasLoaded.value = true
    })
  }
})
</script>
