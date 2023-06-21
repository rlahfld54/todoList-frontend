<template>
  <div id="app" style="margin-top: 60px;">
    <b-container class="bv-example-row">
      <b-row>
        <b-col>
          <b-row>
            <b-col>
              <h1>
                <b-icon-star-fill></b-icon-star-fill>
                투두 리스트
            </h1>
            </b-col>
            <b-col></b-col>
            <b-col>
              <h2><b-icon-calendar2-date-fill></b-icon-calendar2-date-fill></h2>
            </b-col>
          </b-row>

          <b-row class="mt-4">
            <b-col><h5>순수과학,자연과학,자기계발</h5></b-col>
            <b-col></b-col>
            <b-col><h6>+ 새 목록</h6></b-col>
          </b-row>

          <b-tabs content-class="mt-3" fill>
    <b-tab title="First" active><p>I'm the first tab</p></b-tab>
    <b-tab title="Second"><p>I'm the second tab</p></b-tab>
    <b-tab title="Very, very long title"><p>I'm the tab with the very, very long title</p></b-tab>
    <b-tab title="Disabled" disabled><p>I'm a disabled tab!</p></b-tab>
  </b-tabs>


          <b-row class="mt-4">
            <b-col><h4>할 일 2개 남음</h4></b-col>
            <b-col></b-col>
            <b-col><h6><b-icon-arrow-down-up></b-icon-arrow-down-up> 정렬기능</h6></b-col>
          </b-row>

          <b-row class="mt-4">
            <b-col>
              <b-progress :value="value" :max="max" show-progress animated></b-progress>
            </b-col>
            <b-col></b-col>
            <b-col>
              80% 📚📚📚📚📚📚📚📚
            </b-col>
          </b-row>
        </b-col>
      </b-row>

      <b-row class="mt-4 text-center">
        <b-col>
          <b-form-group
      label="오늘의 할 일"
      v-slot="{ ariaDescribedby }"
    >
      <b-form-checkbox-group
        v-model="selected"
        :options="options"
        :aria-describedby="ariaDescribedby"
        name="flavour-2a"
        stacked
      ></b-form-checkbox-group>
    </b-form-group>

        </b-col>
      </b-row>
    </b-container>

    <!-- PostBook -->
    <h1>PostBook</h1>
    <PostBook></PostBook>

    <!-- Calendar.js -->
    <h1>Calendar</h1>
    <Calendar></Calendar>
  </div>
</template>

<script>
import PostBook from "./components/PostBook.vue";
import Calendar from "./components/Calendar.vue";

export default {
  name: 'App',
  components:{
    PostBook,
    Calendar
},
  created(){
    // this.axios.get("http://localhost:8080/api/todo").then((response) => {
    //   console.log(response.data)
    // });
    // var data = {
    //   value: 45,
    //   options:[{ text: '책 먹는 여우', value: 'orange' },
    //       { text: '이상한 나라의 앨리스', value: 'apple' },
    //       { text: 'JAVA의 정석', value: 'pineapple' },
    //       { text: 'Grape', value: 'grape' }]
    // }
  },
  data() {
      return {
        value: 45,
        max: 100,
        selected: [], // Must be an array reference!
        options: [
          { text: '책 먹는 여우', value: 'orange' },
          { text: '이상한 나라의 앨리스', value: 'apple' },
          { text: 'JAVA의 정석', value: 'pineapple' },
          { text: 'Grape', value: 'grape' }
        ]
      }
    },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  /* text-align: center; */
  /* margin-top: 60px; */
  margin: auto;
  width: 900px;
}
</style>
