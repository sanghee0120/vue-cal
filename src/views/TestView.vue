<template>
  <v-calendar
      class="custom-calendar max-w-full"
      :masks="masks"
      :attributes="attributes"
      disable-page-swipe
    >
      <div
        slot="day-content"
        v-on="dayEvents"
        @click="dayClick"
        slot-scope="{ day, attributes }"
        class="flex flex-col h-full z-10 overflow-hidden"
        :class="day.year"
      >
        <span
          class="day-label text-sm text-gray-900"
          :class="[day.dateTime === today ? 'today rounded-sm' : '' ]"
        >{{ day.day }}</span>
        <div class="flex-grow overflow-y-scroll overflow-x-auto">
          <p
            v-for="attr in attributes"
            :key="attr.key"
            class="text-xs leading-tight rounded-sm p-1 mt-0 mb-1"
            :class="attr.customData.class"
          >{{ attr.customData.title }}</p>
        </div>
      </div>
    </v-calendar>
</template>

<script>
export default {
  data() {
    const now = new Date();
    const month = now.getMonth();
    const year = now.getFullYear();
    const day = now.getDate();
    return {
      today: new Date(year, month, day) * 1,
      masks: {
        weekdays: "WWW"
      },
      attributes: [
        {
          key: 1,
          customData: {
            title: "Lunch with mom.",
            class: "bg-red-600 text-white"
          },
          dates: new Date(year, month, 1)
        },
        {
          key: 2,
          customData: {
            title: "Take Noah to basketball practice",
            class: "bg-blue-500 text-white"
          },
          dates: new Date(year, month, 2)
        },
        {
          key: 3,
          customData: {
            title: "Noah's basketball game.",
            class: "bg-blue-500 text-white"
          },
          dates: new Date(year, month, 5)
        },
        {
          key: 4,
          customData: {
            title: "Take car to the shop",
            class: "bg-indigo-500 text-white"
          },
          dates: new Date(year, month, 5)
        },
        {
          key: 4,
          customData: {
            title: "Meeting with new client.",
            class: "bg-teal-500 text-white"
          },
          dates: new Date(year, month, 7)
        },
        {
          key: 5,
          customData: {
            title: "Mia's gymnastics practice.",
            class: "bg-pink-500 text-white"
          },
          dates: new Date(year, month, 11)
        },
        {
          key: 6,
          customData: {
            title: "Cookout with friends.",
            class: "bg-orange-500 text-white"
          },
          dates: { months: 5, ordinalWeekdays: { 2: 1 } }
        },
        {
          key: 7,
          customData: {
            title: "Mia's gymnastics recital.",
            class: "bg-pink-500 text-white"
          },
          dates: new Date(year, month, 22)
        },
        {
          key: 8,
          customData: {
            title: "Visit great grandma.",
            class: "bg-red-600 text-white"
          },
          dates: new Date(year, month, 25)
        },
        {
          key: "today",
          customData: {
            title: "Visit great grandma.",
            class: "bg-red-600 text-white"
          },
          dates: new Date()
        }
      ],
      dayEvents: {
        click: a => {
          // eslint-disable-next-line no-console
          console.log("dayEvents:", a);
        }
      }
    };
  },
  methods: {
    dayClick(a) {
      // eslint-disable-next-line no-console
      console.log("origin DOM click", a);
    }
  }
};
</script>
