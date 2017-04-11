<template>
  <div>
    <div class="page">

      <!-- <button @click="show">
        Contact Us
      </button> -->
    </div>

    <div class="layout">
      <div class="contact-form">

        <label>Пишите нам</label>

        <form class="wrapper" action="">

          <div class="subject">
            <input v-model="subject" type="radio" name="subject" id='idea' value="idea">
            <label for="idea" class="type"> &#9998 Идея </label>
            <input v-model="subject" type="radio" name="subject" id='problem' value='problem'>
            <label for="problem" class="type"> &#9888 Проблема </label>
            <input v-model="subject" type="radio" name="subject" id='qestion' value='qestion'>
            <label for="qestion" class="type"> &#63 Вопрос </label>
            <input v-model="subject" type="radio" name="subject" id='thanks' value='thanks'>
            <label for="thanks" class="type"> &#9829 Спасибо </label>

          </div>

          <div>
              <textarea class="message" v-model="message" rows="8" type="text" required :placeholder="pmessage"/>
          </div>

          <div class="footer">
              <input v-model="email" type="text" required :placeholder="pemail"/>
              <input type="submit" value="Отправить">
          </div>

        </form>
      </div>
    </div>
  </div>
</template>

<script>
  import api from '../../api'

  export default {
    name: 'about-page',
    methods: {
      show() {
      }
    },
    data: () => ({
      email: '',
      message: '',
      subject: 'idea',
      pemail: 'someone@example.com',
      pmessage: 'Я хочу предложить/пожаловаться/помочь/обратить внимание и тд'
    })
  }

  // let $ = s => document.querySelector(s)

  function test() {
    alert(this.innerHTML)
  }

  // $('#idea').onclick = e => {
  //   console.log(e)
  // }

</script>

<style scoped>

  input[type="radio"]{display: none;}

  input[type="radio"]:checked+.type {
    border: 1px solid #ade6b5;
    box-shadow: 0 0 3px 2px #ade6b5;
  }

  .footer{
    display: grid;
    grid-template-columns: 3fr 1fr;
    grid-template-rows: 1fr;
    grid-column-gap: 7em;
    align-items: center
  }


  .subject{
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-around;
    margin: 1em 0;
  }

  .type{
    box-sizing: content-box;
    padding: 0.5em;
    border: 1px solid black;
    cursor: pointer;
    font-family: 'Roboto Slab', serif;
    font-size: 0.9em;
    font-weight: 300;
  }

  .type:hover{
    /*background: #e0cfdf;*/
  }

  label{
    font-size: 1.5em;
    font-family: 'Roboto Slab', serif;
    font-weight: 300;
  }

  input[type=submit]{
    float: right;
    font-size: 1em;
    font-family: 'Roboto Slab', serif;
    font-weight: 300;
    border: 1px solid black;
    background-color: #ade6b5;
    cursor: pointer;
  }

  input[type=text], textarea {
    display: block;
    width: 100%;
    font-family: monospace;
    padding: 0.2em 0.4em;
    line-height: 1.4em;
    margin: 0.5em 0;
    resize: none;
    font-size: 1em;
    font-family: 'Roboto Slab', serif;
    font-weight: 300;
    border: 1px solid black;
  }

  .layout{
    width: 100%;
    min-height: 100%;
    background-color: rgba(0,0,0,0.5);
    overflow: hidden;
    position: fixed;
    top: 0;
    margin-left: -5%;
    /*margin-right: 5%;*/
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .contact-form{
      max-width: 600px;
      width: 90%;
      /*min-width: 550px;*/
      /*height: 450px;*/
      padding:10px;
      background-color: white;
      box-shadow: 0px 0px 10px #000;
      border-top: 6px solid #ade6b5;
  }

  .page {
    margin-left: 1.0em;
    margin-top: 2.5em;
    margin-bottom: 1.5em;
    font-size: 1.1em;
  }

  @media screen and (max-width: 550px) {
    .page {
      /*margin-left: 10px;*/
      /*margin-right: 10px;*/
      font-size: 1em;
    }

    .layout{
      margin-left: 0;
    }
  }
</style>
