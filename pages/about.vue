<template>
<div>
  <v-toolbar
        dark
      >
  
        <v-toolbar-title>About Me</v-toolbar-title>
  
        <v-spacer></v-spacer>

      </v-toolbar>

<v-timeline
    align-top
    :dense="$vuetify.breakpoint.smAndDown"
  >
    <v-timeline-item
      v-for="(item, i) in items"
      :key="i"
      :color="item.color"
      :icon="item.icon"
      :title="item.title"
      fill-dot
    >
      <v-card
        :color="item.color"
        class="ma-3 pa-3"

      >
        <v-card-title style="word-break: normal; color: white">          
          {{item.title}}
        </v-card-title>
      </v-card>
    </v-timeline-item>
  </v-timeline>
  
</div>
</template>

<script>
export default {
  name: 'about',
  data: () => ({
      items: [
        {
          title: 'I was born on May 19, 1996 in Erzincan.',
          color: '#575757',
          icon: 'mdi-baby-buggy',
        },
        {
          title: 'I completed my primary, middle and high school education in Erzincan.',
          color: '#6D3AAC',
          icon: 'mdi-city',
        },
        {
          title: 'I won Balikesir University Electrical and Electronics Engineering and completed my undergraduate education in 2020 with an average of 3.04.',
          color: '#245199',
          icon: 'mdi-book-variant ',
        },
        {
          title: 'I continue my education life by doing my master\'s degree in Erzincan Binali Yildirim University Electrical and Electronics Engineering Department. I am at the thesis stage of my education. (My GPA is 4.00)',
          color: '#6F520B',
          icon: 'mdi-pencil',
        },
        {
          title: 'With my interest in software and my curiosity about the production process of a game, I took part as a trainee in the 7-month bootcamp initiated by the Game and Application Academy. During the bootcamp, I received various trainings such as Unity and Project Management. As a result of the bootcamp, we designed a thriller game called Survival of Fallen with my team of 5 people, where I worked as a developer.',
          color: '#2A652A',
          icon: 'mdi-gamepad',
        },
        {
          title: 'Then I started the YetGen, or Competent Youth program. YetGen is a voluntary education project that takes place at universities and high schools and aims to provide students with the basic competencies they need to have in order to have a successful business life in the 21st century. Within the scope of this program, I took 21st Century competencies courses interactively with selected students like you for ten weeks.',
          color: '#325977',
          icon: 'mdi-laptop',
        },
        {
          title: 'Then I started a 2-month internship at MGS Software software company. During my internship, I received trainings about Vue.js. After my internship, I worked as a Jr. I continue to work as a Front-End Developer.',
          color: '#943B00',
          icon: 'mdi-code-not-equal-variant',
        },
      ],
    }),
}
</script>