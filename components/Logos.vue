<template>
  <div class="logo-container" :class="containerClass">
    <!-- Simple Text Logo -->
    <NuxtLink 
      v-if="variant === 'text'" 
      :to="to" 
      :class="linkClass"
      class="flex items-center space-x-2 text-decoration-none"
    >
      <span class="font-bold" :class="textClass">
        STAY 
        <span class="inline-flex items-center">
          <svg class="w-4 h-4 mx-1" viewBox="0 0 24 24" fill="currentColor">
            <path d="M12 2C13.1 2 14 2.9 14 4C14 5.1 13.1 6 12 6C10.9 6 10 5.1 10 4C10 2.9 10.9 2 12 2M21 9V7L15 1H5C3.9 1 3 1.9 3 3V21C3 22.1 3.9 23 5 23H19C20.1 23 21 22.1 21 21V9H21Z"/>
          </svg>
        </span>
        DRIPPED
      </span>
      <span v-if="showSubtext" :class="subtextClass">MOBILE IV SERVICE</span>
    </NuxtLink>

<!-- Banner Logo -->
<NuxtLink 
  v-else-if="variant === 'banner'" 
  :to="to" 
  :class="linkClass"
  class="block text-decoration-none"
>
  <div class="bg-black text-white px-6 py-3 rounded-lg" :class="bannerClass">
    <div class="flex items-center justify-center space-x-2">
      <span class="font-bold text-xl md:text-2xl">STAY</span>
      <svg class="w-6 h-6" viewBox="0 0 24 24" fill="currentColor">
        <path d="M12 2C13.1 2 14 2.9 14 4C14 5.1 13.1 6 12 6C10.9 6 10 5.1 10 4C10 2.9 10.9 2 12 2M21 9V7L15 1H5C3.9 1 3 1.9 3 3V21C3 22.1 3.9 23 5 23H19C20.1 23 21 22.1 21 21V9H21Z"/>
      </svg>
      <span class="font-bold text-xl md:text-2xl">DRIPPED</span>
    </div>
    <div v-if="showSubtext" class="text-center text-sm tracking-wider mt-1 border-t border-white/30 pt-1">
      — MOBILE IV SERVICE —
    </div>
  </div>
</NuxtLink>

<!-- Circular Logo with Arizona Theme -->
<NuxtLink 
  v-else-if="variant === 'arizona'" 
  :to="to" 
  :class="linkClass"
  class="block text-decoration-none"
>
  <div class="relative" :class="circularClass">
    <!-- Circular Background -->
    <div class="w-24 h-24 md:w-32 md:h-32 rounded-full bg-gradient-to-br from-blue-400 via-pink-300 to-red-400 p-1">
      <div class="w-full h-full rounded-full bg-white flex flex-col items-center justify-center relative overflow-hidden">
        <!-- Desert Scene Background -->
        <div class="absolute inset-0 bg-gradient-to-b from-pink-200 via-orange-200 to-blue-300"></div>
        
        <!-- Mountains -->
        <div class="absolute bottom-8 left-1/2 transform -translate-x-1/2">
          <div class="w-8 h-4 bg-red-400 transform rotate-12"></div>
          <div class="w-6 h-3 bg-red-500 transform -rotate-12 -mt-2 ml-2"></div>
        </div>
        
        <!-- Cacti -->
        <div class="absolute bottom-4 left-2">
          <div class="w-1 h-4 bg-green-700"></div>
          <div class="w-1 h-2 bg-green-700 absolute top-1 -left-1"></div>
          <div class="w-1 h-2 bg-green-700 absolute top-2 left-1"></div>
        </div>
        <div class="absolute bottom-4 right-2">
          <div class="w-1 h-3 bg-green-700"></div>
          <div class="w-1 h-1 bg-green-700 absolute top-1 -left-0.5"></div>
        </div>
        
        <!-- Cowboy on Horse Silhouette -->
        <div class="absolute bottom-6 left-1/2 transform -translate-x-1/2 z-10">
          <div class="text-black text-xs">🤠🐎💉</div>
        </div>
        
        <!-- IV Bag Icon -->
        <div class="absolute top-2 left-1/2 transform -translate-x-1/2 z-10">
          <svg class="w-4 h-4 text-blue-600" viewBox="0 0 24 24" fill="currentColor">
            <path d="M12 2C13.1 2 14 2.9 14 4C14 5.1 13.1 6 12 6C10.9 6 10 5.1 10 4C10 2.9 10.9 2 12 2M21 9V7L15 1H5C3.9 1 3 1.9 3 3V21C3 22.1 3.9 23 5 23H19C20.1 23 21 22.1 21 21V9H21Z"/>
          </svg>
        </div>
      </div>
    </div>
    
    <!-- Text Below Circle -->
    <div class="text-center mt-2">
      <div class="font-bold text-black text-sm">STAY DRIPPED</div>
      <div v-if="showSubtext" class="text-xs text-gray-600">MOBILE IV SERVICE</div>
    </div>
  </div>
</NuxtLink>

<!-- Full Image Logo -->
<NuxtLink 
  v-else 
  :to="to" 
  :class="linkClass"
  class="block text-decoration-none"
>
  <img 
    :src="logoSrc" 
    :alt="alt"
    :class="imageClass"
    class="object-contain"
  >
</NuxtLink>

  </div>
</template>

<script setup>
const props = defineProps({
  // Logo variant type
  variant: {
    type: String,
    default: 'image', // 'image', 'text', 'banner', 'arizona'
    validator: (value) => ['image', 'text', 'banner', 'arizona'].includes(value)
  },
  
  // Link destination
  to: {
    type: String,
    default: '/'
  },
  
  // Logo source for image variant
  logoSrc: {
    type: String,
    default: 'https://staydrippediv.com/wp-content/uploads/2024/05/Stay-Dripped-IV-Logo.png'
  },
  
  // Alt text
  alt: {
    type: String,
    default: 'Stay Dripped IV Logo'
  },
  
  // Size presets
  size: {
    type: String,
    default: 'medium', // 'small', 'medium', 'large'
    validator: (value) => ['small', 'medium', 'large'].includes(value)
  },
  
  // Show subtext
  showSubtext: {
    type: Boolean,
    default: true
  },
  
  // Custom classes
  containerClass: {
    type: String,
    default: ''
  },
  
  linkClass: {
    type: String,
    default: ''
  }
})

// Computed classes based on size and variant
const imageClass = computed(() => {
  const sizes = {
    small: 'h-8 w-auto',
    medium: 'h-10 w-auto lg:h-12',
    large: 'h-16 w-auto lg:h-20'
  }
  return sizes[props.size] || sizes.medium
})

const textClass = computed(() => {
  const sizes = {
    small: 'text-lg',
    medium: 'text-xl lg:text-2xl',
    large: 'text-2xl lg:text-3xl'
  }
  return `${sizes[props.size] || sizes.medium} text-blue-600`
})

const subtextClass = computed(() => {
  const sizes = {
    small: 'text-xs',
    medium: 'text-sm',
    large: 'text-base'
  }
  return `${sizes[props.size] || sizes.medium} text-gray-600 tracking-wider`
})

const bannerClass = computed(() => {
  const sizes = {
    small: 'px-4 py-2',
    medium: 'px-6 py-3',
    large: 'px-8 py-4'
  }
  return sizes[props.size] || sizes.medium
})

const circularClass = computed(() => {
  const sizes = {
    small: 'w-16',
    medium: 'w-24 md:w-32',
    large: 'w-32 md:w-40'
  }
  return sizes[props.size] || sizes.medium
})
</script>

<style scoped>
.logo-container {
  display: inline-block;
}

.text-decoration-none {
  text-decoration: none;
}

/* Hover effects */
.logo-container a:hover {
  transform: scale(1.05);
  transition: transform 0.3s ease;
}

/* Arizona theme animations */
@keyframes desert-wind {
  0%, 100% { transform: translateX(0px); }
  50% { transform: translateX(2px); }
}

.variant-arizona:hover .absolute {
  animation: desert-wind 2s ease-in-out infinite;
}
</style>
