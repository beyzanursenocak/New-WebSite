<template>
    <v-card
      class="mx-auto"
      style="background-color: #F4F9F4;"
    >
  
      <v-toolbar
      light
      color="#F4F9F4"
      >
  
        <v-toolbar-title color="#F6F4EB">Projects</v-toolbar-title>

        <v-spacer></v-spacer>
        
        <v-menu offset-y>
    <template #activator="{ on }">
      <v-btn v-on="on"
      color="#5C8D89"
      rounded
      aria-label="Categories"
      >
        Categories
      </v-btn>
    </template>

    <v-list>
      <v-list-item v-for="(category, index) in categories" :key="index" @click="filterProjects(category)">
        <v-list-item-title>
          {{ category }}
        </v-list-item-title>
      </v-list-item>
    </v-list>
  </v-menu>

      </v-toolbar>
      <v-spacer></v-spacer>
      <v-container fluid>
        <v-row dense>
          <v-col
            v-for="project in filteredProjects" :key="project.id"
            :title="project.title"
            :icon="project.icon"
            cols="12"
            md="4"
          >
            <v-card style="background-color: #d6ddd6;">
              <nuxt-img
                :src="require(`@/assets/images/portfolio/${project.src}`)"
                :alt="project.title"
                class="img"
                formats="webp"
                preload
                loading="lazy"
                sizes="sm:100vw md:50vw lg:400px"
                layout="responsive"
              ></nuxt-img>
              <v-card-actions>
                <v-btn :aria-label="project.title"  style="background-color: #5C8D89;">
              <h6 @click="goPage(project.link)"><v-icon> mdi-link-variant </v-icon> {{ project.title }} </h6>
                </v-btn> 
                <v-btn icon :aria-label="project.title">
                  <v-icon 
                  @click="toggleShow(project)">{{ project.icon }}</v-icon>
                </v-btn>
              </v-card-actions>

                <v-expand-transition>
                  <div v-show="project.show">
                    <v-divider></v-divider>
                    <v-card-text>
                      {{ project.text }}
                    </v-card-text>
                 </div>
                </v-expand-transition>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-card>
  </template>

<script>

export default {
  
  data: () => ({
    projects: [
      { title: 'Cryptocurrency', src: 'Cryptocurrency.webp', icon: 'mdi-chart-line' , link: 'https://github.com/Firdesbeyzanur/Cryptocurrency' , text: 'Cryptocurrency exchange tracking in a table with information pulled from the API.' , flex: 4 , show: false, categories: ['Vue.js', 'All'] },
      { title: 'Food Blog', src: 'Food Blog.webp', icon: 'mdi-food' , link: 'https://github.com/Firdesbeyzanur/Food-App' , text: 'A blog with dessert recipes.' , flex: 4 , show: false, categories: ['Vue.js', 'All'] },
      { title: 'CarTrader', src: 'CarTrader.webp', icon: 'mdi-car' , link: 'https://github.com/Firdesbeyzanur/CarTrader' , text: 'It\'s an app for buying a car. More useful with filtering feature.' , flex: 4 , show: false, categories: ['Vue.js', 'All'] },
      { title: 'Find the Hulk', src: 'Find the Hulk.webp', icon: 'mdi-cat' , link: 'https://github.com/Firdesbeyzanur/Hulku-Bul' , text: 'It\'s a sticky memory game for my cat. Guess what\'s on the face-down card.' , flex: 4 , show: false, categories: ['Vue.js', 'All']  },
      { title: 'Website', src: 'Website.webp', icon: 'mdi-ghost' , link: 'https://github.com/Firdesbeyzanur/Nuxtjs-WebSite' , text: 'My first mini website I made using Nuxt.' , flex: 4 , show: false, categories: ['Nuxt.js', 'All'] },
      { title: 'Website - 2', src: 'Website - 2.webp', icon: 'mdi-responsive' , link: 'https://github.com/Firdesbeyzanur/ResponsiveWebsite' , text: 'Responsive site created with only HTML and CSS.' , flex: 4 , show: false, categories: ['HTML', 'All'] },
      { title: 'Website - 3', src: 'Website - 3.webp', icon: 'mdi-laptop' , link: 'https://github.com/Firdesbeyzanur/ResponsiveWebsite-2' , text: 'Responsive site created with only HTML and CSS.' , flex: 4 , show: false, categories: ['HTML', 'All'] },
      { title: 'Website - 4', src: 'ResponsiveWebsite-1.webp', icon: 'mdi-laptop' , link: 'https://github.com/Firdesbeyzanur/ResponsiveWebsite' , text: 'Responsive website made using only HTML, CSS and Javascript.' , flex: 4 , show: false, categories: ['HTML','JavaScript', 'All'] },
      { title: 'Website - 5', src: 'ResponsiveWebsite-2.webp', icon: 'mdi-laptop' , link: 'https://github.com/Firdesbeyzanur/ResponsiveWebsite-2' , text: 'Responsive website made using only HTML and CSS.' , flex: 4 , show: false, categories: ['HTML', 'All'] },
      { title: 'Unity Game', src: 'Unity Game.webp', icon: 'mdi-gamepad-variant' , link: 'https://github.com/Firdesbeyzanur/Survival-of-The-Fallen' , text: 'It is a thriller game that we developed with my team of 5 people, which I worked as a developer during the Oyun ve Uygulama Akademisi bootcamp process.' , flex: 4 , show: false, categories: ['Unity', 'All'] },
      { title: 'My Application', src: 'My Application.webp', icon: 'mdi-airballoon' , link: 'https://github.com/Firdesbeyzanur/Vue3-Pictures' , text: 'An app to upload and delete photos.' , flex: 4 , show: false, categories: ['Vue.js', 'All'] },
      { title: 'Note Application', src: 'Note Application.webp', icon: 'mdi-clipboard-check' , link: 'https://github.com/Firdesbeyzanur/FireBase-NotesApp' , text: 'Do you forget things to do during the day? Then this note app is for you.' , flex: 4 , show: false, categories: ['Vue.js', 'All'] },
      { title: 'Form List', src: 'Form List.webp', icon: 'mdi-account-key' , link: 'https://github.com/Firdesbeyzanur/Form' , text: 'Form application. Enter your information, click on the button and your information will come back on the card.' , flex: 4 , show: false, categories: ['Vue.js', 'All'] },
      { title: 'Number App', src: 'Number App.webp', icon: 'mdi-code-equal' , link: 'https://github.com/Firdesbeyzanur/Nuxt-RandomNumber' , text: 'An application to generate random comma and whole numbers.' , flex: 4 , show: false, categories: ['Nuxt.js', 'All'] },
      { title: 'Blog', src: 'Blog.webp', icon: 'mdi-gmail' , link: 'https://github.com/Firdesbeyzanur/WebSite' , text: 'I was asked for a blog page. A blog with a login page and admin login.' , flex: 4 , show: false, categories: ['Vue.js', 'All'] },
      { title: 'Card App - 1', src: 'Card App - 1.webp', icon: 'mdi-newspaper' , link: 'https://github.com/Firdesbeyzanur/Card-App-4' , text: 'A card app with additional features in the edit section with description section and change image section.' , flex: 4 , show: false, categories: ['Vue.js', 'All'] },
      { title: 'Card App - 2', src: 'Card App - 2.webp', icon: 'mdi-arrange-bring-forward' ,  link: 'https://github.com/Firdesbeyzanur/Card-App-3' , text: 'A card app with a description section and an edit section.' ,flex: 4 , show: false, categories: ['Vue.js', 'All'] },
      { title: 'Card App - 3', src: 'Card App - 3.webp', icon: 'mdi-arrange-send-to-back' , link: 'https://github.com/Firdesbeyzanur/AddImageCard' , text: 'An application where you can upload up to 10 pieces with pictures and enter your information.' , flex: 4 , show: false, categories: ['Vue.js', 'All'] },
      { title: 'Card App - 4', src: 'Card App - 4.webp', icon: 'mdi-arrange-bring-to-front' , link: 'https://github.com/Firdesbeyzanur/Card-App-2' , text: 'Click on the pen to open the edit section and edit it.' , flex: 4 , show: false, categories: ['Vue.js', 'All'] },
      { title: 'Card App - 5', src: 'Card App - 5.webp', icon: 'mdi-multiplication-box' , link: 'https://github.com/Firdesbeyzanur/Card-App-1' , text: 'Edit the information on the card however you like.' , flex: 4 , show: false, categories: ['Vue.js', 'All'] },
      { title: 'To-Do List', src: 'ToDoList.webp', icon: 'mdi-format-list-group' , link: 'https://github.com/Firdesbeyzanur/Todo-List' , text: 'Made a To-Do list with JavaScript.' , flex: 4 , show: false, categories: ['JavaScript', 'All'] },
      { title: 'Auto Gallery', src: 'AutoGallery.webp', icon: 'mdi-car-estate' , link: 'https://github.com/Firdesbeyzanur/AutoGallery' , text: 'A car site with a car name, picture and price added with JavaScript.' , flex: 4 , show: false, categories: ['HTML', 'JavaScript', 'All'] },
      { title: 'Titanic', src: 'Titanic.webp', icon: 'mdi-chat' , link: 'https://github.com/Firdesbeyzanur/TitanicDataset' , text: 'In the Titanic dataset, data preprocessing was performed, ExtraTressClassifier and Feature Importance were extracted, SelectKBest was scored, correlation maps were created, non-normally distributed data were standardized and basic statistical information was extracted.' , flex: 4 , show: false, categories: ['Python', 'All'] },
      { title: 'Insurance', src: 'Insurance.webp', icon: 'mdi-clipboard-plus' , link: 'https://github.com/Firdesbeyzanur/InsuranceDataset' , text: 'In the insurance dataset, prediction was performed with classifiers, Accuracy, Precision, Recall, F1-Score results were tabulated and confusion matrix was plotted.' , flex: 4 , show: false, categories: ['Python', 'All'] },
      { title: 'Stock', src: 'Stock.webp', icon: 'mdi-cash' , link: 'https://github.com/Firdesbeyzanur/StockDataset' , text: 'Time Series, Regression and LSTM analysis were performed on the stock market data set and ARIMA model was applied.' , flex: 4 , show: false, categories: ['Python', 'All'] },
      { title: 'Forecast Process', src: 'Forecast Process.webp', icon: 'mdi-account-convert' , link: 'https://github.com/Firdesbeyzanur/Tahminleme-Islemi' , text: 'Python code that predicts the age, race and gender of people after various operations.' , flex: 4 , show: false, categories: ['Python', 'All'] },
      { title: 'Face Matching', src: 'Face Matching.webp', icon: 'mdi-account-circle' , link: 'https://github.com/Firdesbeyzanur/Yuz-Eslestirme' , text: 'Face matching of the people in the database was done using MATLAB.' , flex: 4 , show: false, categories: ['MATLAB', 'All'] },
      { title: 'Prediction', src: 'Prediction.webp', icon: 'mdi-account-multiple' , link: 'https://github.com/Firdesbeyzanur/Prediction-Classification' , text: 'A program that predicts people\'s age, gender and ethnicity with Python' , flex: 4 , show: false, categories: ['Python', 'All'] },
      { title: 'Mushroom Class', src: 'Mushroom Class.webp', icon: 'mdi-mushroom' , link: 'https://github.com/Firdesbeyzanur/Mushroom-classification' , text: 'In this project, we will use the "Mushroom Classification" dataset, a public dataset from kaggle.com, and try to figure out whether a mushroom is edible or not.' , flex: 4 , show: false, categories: ['Python', 'All'] },
      { title: 'Insurance', src: 'Insurance - 2.webp', icon: 'mdi-clipboard-account' , link: 'https://github.com/Firdesbeyzanur/GlobalAIHub-Project' , text: 'The insurance dataset was examined at the bootcamp organized by Global AI Hub.' , flex: 4 , show: false, categories: ['Python', 'All']},
      { title: 'Date Fruit', src: 'Date Fruit.webp', icon: 'mdi-food-apple' , link: 'https://github.com/Firdesbeyzanur/Deep-Learning' , text: 'We created a neural network to classify dates with TensorFlow. For this, we used the "Date Fruit Dataset" available on Kaggle.' , flex: 4 , show: false, categories: ['Python', 'All'] },
      { title: 'Image Class', src: 'Image Class.webp', icon: 'mdi-grid' , link: 'https://github.com/Firdesbeyzanur/CNN' , text: 'In this project, we built a convolutional neural network to solve a multi-class image classification problem.' , flex: 4 , show: false, categories: ['Python', 'All'] },
      { title: 'Movie Review', src: 'Movie Review.webp', icon: 'mdi-movie' , link: 'https://github.com/Firdesbeyzanur/Deep-Learning_2' , text: 'Recurrent neural networks. IMDB Movie Review Dataset was used.' , flex: 4 , show: false, categories: ['Python', 'All']},
      { title: 'Puzzle', src: 'Puzzle.webp', icon: 'mdi-puzzle' , link: 'https://github.com/Firdesbeyzanur/Lena512Disassembly' , text: 'Lena512 image split into 4 parts with MATLAB.' , flex: 4 , show: false, categories: ['MATLAB', 'All']},
      { title: 'Frame', src: 'Frame.webp', icon: 'mdi-image-filter-frames' , link: 'https://github.com/Firdesbeyzanur/Lena512Frame' , text: 'We have the Lena512 picture in a black frame.' , flex: 4 , show: false, categories: ['MATLAB', 'All']},
      { title: 'Round Frame', src: 'Round Frame.webp', icon: 'mdi-checkbox-blank-circle' , link: 'https://github.com/Firdesbeyzanur/Lena512RoundFrame' , text: 'We have enclosed the Lena512 picture in a black round frame.' , flex: 4 , show: false, categories: ['MATLAB', 'All']},
      { title: 'Resolution', src: 'Resolution.webp', icon: 'mdi-file-image' , link: 'https://github.com/Firdesbeyzanur/Lena512Resolution' , text: 'We have output the Lena512 image in different resolutions.' , flex: 4 , show: false, categories: ['MATLAB', 'All']},
      { title: 'Xray Image', src: 'Xray Image.webp', icon: 'mdi-hospital' , link: 'https://github.com/Firdesbeyzanur/XrayImageLesion' , text: 'The negative of the xray image was taken, the lesion was circled, spanned in the gray level range of 0.5-0.75, and the negative and gray level range were combined. ' , flex: 4 , show: false, categories: ['MATLAB', 'All']},
      { title: 'Histogram', src: 'Histogram.webp', icon: 'mdi-chart-histogram' , link: 'https://github.com/Firdesbeyzanur/Histogram' , text: 'We got the input and output histogram images of the image. ' , flex: 4 , show: false, categories: ['MATLAB', 'All']},
    ],
    categories: [ 'All', 'HTML', 'Vue.js', 'Nuxt.js','Unity', 'Python', 'MATLAB', 'JavaScript'],
    selectedCategory: null
  }),
  computed: {
      filteredProjects() {
        if (!this.selectedCategory) {
          return this.projects;
        }
        return this.projects.filter(project => project.categories.includes(this.selectedCategory));
      }
    },
  methods: {
    goPage: function (link) {
      window.open(link, '_blank');
    },
    toggleShow(project) {
      project.show = !project.show;
    },
    filterProjects(category) {
        this.selectedCategory = category;
      },
  }
}
</script>

<style scoped>
.img {
  width: 100%;
  height: 250px;
  object-fit: cover;
}
</style>
