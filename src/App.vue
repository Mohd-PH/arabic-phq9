<template>
  <div id="app" dir="rtl">
    <nav class="navbar fixed-top navbar-light bg-light">
      <a class="navbar-brand" href="#">إستبيان حول صحة المريض 9</a>
    </nav>
    <div class="alert alert-success" role="alert">
      <h4 class="alert-heading">تنبيه!</h4>
      <p>هذا الإستبيان لا يجمع البيانات، لا تنسى مشاركة نتيجتك مع الطبيب المعالج</p>
    </div>
    <h3>
      كم مرة عانيت من الأعراض التالية خلال
      <u>الأسبوعين الماضية</u>
    </h3>
    <hr>
    <div class="question" v-for="(question, i) in questions" :key="i">
      <p v-text="question.question"></p>
      <div class="btn-group" role="group" aria-label="Basic example">
        <button
          type="button"
          :class="{btn:true, 'btn-secondary': 0 !== question.selected,'btn-primary': 0 === question.selected}"
          @click="optionClicked(i,0)"
        >أبدا</button>
        <button
          type="button"
          :class="{btn:true, 'btn-secondary': 1 !== question.selected,'btn-primary': 1 === question.selected}"
          @click="optionClicked(i,1)"
        >بعض الأيام</button>
        <button
          type="button"
          :class="{btn:true, 'btn-secondary': 2 !== question.selected,'btn-primary': 2 === question.selected}"
          @click="optionClicked(i,2)"
        >أكثر من نصف الأيام</button>
        <button
          type="button"
          :class="{btn:true, 'btn-secondary': 3 !== question.selected,'btn-primary': 3 === question.selected}"
          @click="optionClicked(i,3)"
        >كل الأيام</button>
      </div>
      <hr>
    </div>
    <p id="result">النتيجة {{result}}</p>
  </div>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
      questions: [
        {
          question: 'قلة الإهتمام بممارسة الأشياء',
          selected: 0
        },
        {
          question: 'الشعور بالحزن أو ضيق الصدر أو اليأس',
          selected: 0
        },
        {
          question:
            'الصعوبة في الركون إلى النوم أو النوم بإنتظام أو النوم أكثر من العادة',
          selected: 0
        },
        {
          question: 'الشعور بالتعب أو بقلة الحيوية',
          selected: 0
        },
        {
          question: 'قلة الشهية أو كثرة الأكل',
          selected: 0
        },
        {
          question: 'الشعور بعدم الرضا عن النفس أو بالفشل أو الإحباط تجاه ذويك',
          selected: 0
        },
        {
          question:
            'الصعوبة في التركيز على الأشياء, مثل قرائة الصحف أو مشاهدة التليفزيون',
          selected: 0
        },
        {
          question:
            'بطء في الحركة أو الكلام بدرجة ملحوظة من الآخرين؟ أو على العكس من ذلك كثرة التململ والتحرك إلى درجة فوق العادة',
          selected: 0
        },
        {
          question: 'الشعور بتفضيل الموت عن الحياة أو بإيذاء النفس بطريقة ما',
          selected: 0
        }
      ]
    }
  },
  methods: {
    optionClicked (questionId, optionSelected) {
      this.questions[questionId].selected = optionSelected
    }
  },
  computed: {
    result () {
      return this.questions.reduce((total, question) => {
        return total + question.selected
      }, 0)
    }
  }
}
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding-top: 80px;
}

.navbar {
  border-bottom: 1px #eeeeee solid;
  box-shadow: 0 3px 2px -3px rgba(0, 0, 0, 0.3);
}

h1 {
  margin-bottom: 24px;
}
.question p {
  font-size: 22px;
}

#result {
  font-size: 28px;
  margin: 22px;
}
.btn-group .btn {
  border: 1px solid white !important;
}
</style>
