<template>
  <div class="card mt-2" v-if="tasks.length && show">
    <ul class="list-group list-group-flush">
      <Task v-for="task in tasks" 
            :key="task.id" 
            :task="task" 
            @updated="$emit('updated', $event)"
            @completed="$emit('completed', $event)"
            @deleted="$emit('deleted', $event)"
      />
    </ul> 
  </div>
</template>

<script setup>
import Task from '@/components/tasks/Task.vue'

defineProps({
  tasks: {
    type: Array,
    required: true
  },
  show: {
    type: Boolean,
    default: true
  }
})
</script>