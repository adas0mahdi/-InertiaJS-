<template>
    <Head title="home" />
      <MonitorList :monitors="monitors" />
  </template>
  
  <script setup>
  import MonitorList from '@/components/home/MonitorList.vue';
  import { Head } from '@inertiajs/vue3';
  defineProps(["monitors"])
  </script>
  
