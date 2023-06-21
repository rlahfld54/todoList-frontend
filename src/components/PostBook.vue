<template>
    <div>
      <b-form-rating v-model="star" variant="warning" class="mb-2"></b-form-rating>
        <b-form @submit="onSubmit" @reset="onReset" v-if="show">
            <b-form-group id="input-group-3" label="도서 카테고리" label-for="input-3">
                <b-form-select
                id="input-3"
                v-model="form.food"
                :options="foods"
                required
                ></b-form-select>
            </b-form-group>

            <img src="http://image.aladin.co.kr/product/10513/92/cover/8998751208_1.jpg" alt="">
      
        <b-form-group id="input-group-2" label="책 제목" label-for="input-2">
            <b-form-input
            id="input-2"
            v-model="inputData"
            placeholder="책 제목을 입력하세요"
            required
            ></b-form-input>
        </b-form-group>
        <button @click="test">전송</button>

        <b-card bg-variant="warning" text-variant="white" header="자동완성 기능" class="text-center mt-4">
        <b-card-text>
          <ul>
            <li v-for="item in resultList" :key="item.id">
              {{ item }}
            </li>
          </ul>
        </b-card-text>
      </b-card>

        <div>
            <p>책 읽을 날짜</p>
            <input type="date" name="" id="" v-model="form.value1"/>
            <input type="date" name="" id=""  v-model="form.secondvalue"/>
        </div>

        <b-form-group
            id="input-group-1"
            label="지은이"
            label-for="input-1"
        >
            <b-form-input
            id="input-1"
            v-model="form.email"
            placeholder="내용을 입력해주세요"
            required
            ></b-form-input>
        </b-form-group>

        <b-form-group
            id="input-group-1"
            label="출판사"
            label-for="input-1"
        >
            <b-form-input
            id="input-1"
            v-model="form.company"
            placeholder="내용을 입력해주세요"
            required
            ></b-form-input>
        </b-form-group>

        <label for="메모"></label>
        <textarea name="" id="" cols="30" rows="10" v-model="form.memo"></textarea>

      <b-button type="submit" variant="primary">수정</b-button>
      <b-button type="reset" variant="danger">삭제</b-button>
    </b-form>
    <b-card class="mt-3" header="Form Data Result">
      <pre class="m-0">{{ form }}</pre>
    </b-card>
    </div>
</template>
<script>
export default {
  name: 'PostBook',
  created(){
    // this.axios.get("https://www.nl.go.kr/NL/search/openApi/search.do?key=a29b041386e3197429c36f81b0dc7354c5154ee69f0c2279234a9048c54cdce2&kwd=%ED%86%A0%EC%A7%80").then((response) => {
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
        form: {
          email: '',
          name: '',
          food: null,
          company:'',
          value1:"",
          secondvalue:"",
            memo:"",
            bookimg:"",
        },
        foods: [{ text: '도서 카테고리', value: null }, '자기계발', '자연과학', '한국소설', '지리'],
        show: true,
        star: 3,
        inputData:"",
        resultList:[]
      }
    },
    watch:{
      inputData(e){
        console.log(e)
        this.axios.get("http://localhost:8081/api/todo/search?str="+ e ,{
          headers:{
            'Access-Control-Allow-Origin': '*',
            'Content-Type': 'application/json; charset = utf-8'
          }
        }).then((response) => {
            // console.log(response.data)
            console.log(response)
          });
      }
    },
    methods: {
      onSubmit(event) {
        event.preventDefault()
        alert(JSON.stringify(this.form))
      },
      onReset(event) {
        event.preventDefault()
        // Reset our form values
        this.form.email = ''
        this.form.name = ''
        this.form.food = null
        this.form.checked = []
        // Trick to reset/clear native browser form validation state
        this.show = false
        this.$nextTick(() => {
          this.show = true
        })
      },
      test(){
        this.axios.get("http://localhost:8081/api/todo/search",{
          headers:{
            'Access-Control-Allow-Origin': '*',
            'Content-Type': 'application/json; charset = utf-8'
          }
        }).then((response) => {
            // console.log(response.data)
            console.log(response)
          });
      }
    }
}
</script>