<template>
  <div class="grid-container">
    <div class="grid-item">
      <div class="card-details">
        <img class="avatar" :src="IconJeremy" alt="avatar">
        <p>Report for</p><h2>Jeremy Robson</h2>
      </div>
      <div class="card-background">
        <h3><span @click="selectedOption = 'daily'" :class="{ option: true, active: selectedOption === 'daily' }">Daily</span></h3>
        <h3><span @click="selectedOption = 'weekly'" :class="{ option: true, active: selectedOption === 'weekly' }">Weekly</span></h3>
        <h3><span @click="selectedOption = 'monthly'" :class="{ option: true, active: selectedOption === 'monthly' }">Monthly</span></h3>
      </div>
    </div>
    <div class="grid-item" v-for="activity in activities" :key="activity.title" :style="{ backgroundImage: `url(${activity.iconUrl})`, backgroundColor: activity.backgroundColor }">
      <div class="card-background"></div>
      <div class="card-details">
        <div class="card-header">
        <h3>{{ activity.title }}</h3><img class="dots" :src="IconEllipsis" alt="menu"></div>
        <div v-if="selectedOption" class="card-time">
          <h1>{{ activity.timeframes[selectedOption].current }}hrs</h1>
          <p> {{ previously }} - {{ activity.timeframes[selectedOption].previous }}hrs</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue';
import IconWork from "./assets/icon-work.svg";
import IconPlay from "./assets/icon-play.svg";
import IconStudy from "./assets/icon-study.svg";
import IconExercise from "./assets/icon-exercise.svg";
import IconSocial from "./assets/icon-social.svg";
import IconSelfCare from "./assets/icon-self-care.svg";
import IconJeremy from "./assets/image-jeremy.png";
import IconEllipsis from "./assets/icon-ellipsis.svg";

let selectedOption = ref('daily');

const activities = ref([
  {
    "title": "Work",
    "iconUrl": IconWork,
    "backgroundColor": "hsl(15, 100%, 70%)",
    "timeframes": {
      "daily": {
        "current": 5,
        "previous": 7
      },
      "weekly": {
        "current": 32,
        "previous": 36
      },
      "monthly": {
        "current": 103,
        "previous": 128
      }
    }
  },
  {
    "title": "Play",
    "iconUrl": IconPlay,
    "backgroundColor": "hsl(195, 74%, 62%)",
    "timeframes": {
      "daily": {
        "current": 1,
        "previous": 2
      },
      "weekly": {
        "current": 10,
        "previous": 8
      },
      "monthly": {
        "current": 23,
        "previous": 29
      }
    }
  },
  {
    "title": "Study",
    "iconUrl": IconStudy,
    "backgroundColor": "hsl(348, 100%, 68%)",
    "timeframes": {
      "daily": {
        "current": 0,
        "previous": 1
      },
      "weekly": {
        "current": 4,
        "previous": 7
      },
      "monthly": {
        "current": 13,
        "previous": 19
      }
    }
  },
  {
    "title": "Exercise",
    "iconUrl": IconExercise,
    "backgroundColor": "hsl(145, 58%, 55%)",
    "timeframes": {
      "daily": {
        "current": 1,
        "previous": 1
      },
      "weekly": {
        "current": 4,
        "previous": 5
      },
      "monthly": {
        "current": 11,
        "previous": 18
      }
    }
  },
  {
    "title": "Social",
    "iconUrl": IconSocial,
    "backgroundColor": "hsl(264, 64%, 52%)",
    "timeframes": {
      "daily": {
        "current": 1,
        "previous": 3
      },
      "weekly": {
        "current": 5,
        "previous": 10
      },
      "monthly": {
        "current": 21,
        "previous": 23
      }
    }
  },
  {
    "title": "Self Care",
    "iconUrl": IconSelfCare,
    "backgroundColor": "hsl(43, 84%, 65%)",
    "timeframes": {
      "daily": {
        "current": 0,
        "previous": 1
      },
      "weekly": {
        "current": 2,
        "previous": 2
      },
      "monthly": {
        "current": 7,
        "previous": 11
      }
    }
  }
]);
const previously = computed(() => {
  switch (selectedOption.value) {
    case 'daily':
      return 'Yesterday'
    case 'weekly':
      return 'Last week'
    case 'monthly':
      return 'Last month'
    default:
      return 'Unknown'
  }
})
</script>
