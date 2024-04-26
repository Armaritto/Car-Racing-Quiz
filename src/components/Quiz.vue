<template>
  <div class="main-class">
    <div class="question-partition">
      <div class="teams">
        <div @click="fadeOthers($event)">أولى ولاد</div>
        <div @click="fadeOthers($event)">أولى بنات</div>
        <div @click="fadeOthers($event)">تانية ولاد</div>
        <div @click="fadeOthers($event)">تانية بنات</div>
        <div @click="fadeOthers($event)">تالتة ولاد</div>
        <div @click="fadeOthers($event)">تالتة بنات</div>
      </div>
      <div class="categories" v-if="oula_welad">
        <div class="text" v-bind:class="{ fade: categories['أولى ولاد'][1] }" @click="toggleCategory('أولى ولاد', 1)">القيامة 1</div>
        <div class="text" v-bind:class="{ fade: categories['أولى ولاد'][2] }" @click="toggleCategory('أولى ولاد', 2)">القيامة 2</div>
        <div class="text" v-bind:class="{ fade: categories['أولى ولاد'][3] }" @click="toggleCategory('أولى ولاد', 3)">القيامة 3</div>
        <div class="text" v-bind:class="{ fade: categories['أولى ولاد'][4] }" @click="toggleCategory('أولى ولاد', 4)">طقس</div>
        <div class="text" v-bind:class="{ fade: categories['أولى ولاد'][5] }" @click="toggleCategory('أولى ولاد', 5)">شخصيات كتابية</div>
        <div class="text" v-bind:class="{ fade: categories['أولى ولاد'][6] }" @click="toggleCategory('أولى ولاد', 6)">معلومات عامة</div>
      </div>
      <div class="categories" v-else-if="oula_banat">
        <div class="text" v-bind:class="{ fade: categories['أولى بنات'][1] }" @click="toggleCategory('أولى ولاد', 1)"> القيامة 1</div>
        <div class="text" v-bind:class="{ fade: categories['أولى بنات'][2] }" @click="toggleCategory('أولى بنات', 2)"> القيامة 2</div>
        <div class="text" v-bind:class="{ fade: categories['أولى بنات'][3] }" @click="toggleCategory('أولى بنات', 3)"> القيامة 3</div>
        <div class="text" v-bind:class="{ fade: categories['أولى بنات'][4] }" @click="toggleCategory('أولى بنات', 4)">طقس</div>
        <div class="text" v-bind:class="{ fade: categories['أولى بنات'][5] }" @click="toggleCategory('أولى بنات', 5)">شخصيات كتابية</div>
        <div class="text" v-bind:class="{ fade: categories['أولى بنات'][6] }" @click="toggleCategory('أولى بنات', 6)">معلومات عامة</div>
      </div>
      <div class="categories" v-if="tanya_welad">
        <div class="text" v-bind:class="{ fade: categories['تانية ولاد'][1] }" @click="toggleCategory('تانية ولاد', 1)"> القيامة 1</div>
        <div class="text" v-bind:class="{ fade: categories['تانية ولاد'][2] }" @click="toggleCategory('تانية ولاد', 2)"> القيامة 2</div>
        <div class="text" v-bind:class="{ fade: categories['تانية ولاد'][3] }" @click="toggleCategory('تانية ولاد', 3)"> القيامة 3</div>
        <div class="text" v-bind:class="{ fade: categories['تانية ولاد'][4] }" @click="toggleCategory('تانية ولاد', 4)">طقس</div>
        <div class="text" v-bind:class="{ fade: categories['تانية ولاد'][5] }" @click="toggleCategory('تانية ولاد', 5)">شخصيات كتابية</div>
        <div class="text" v-bind:class="{ fade: categories['تانية ولاد'][6] }" @click="toggleCategory('تانية ولاد', 6)">معلومات عامة</div>
      </div>
      <div class="categories" v-if="tanya_banat">
        <div class="text" v-bind:class="{ fade: categories['تانية بنات'][1] }" @click="toggleCategory('تانية بنات', 1)"> القيامة 1</div>
        <div class="text" v-bind:class="{ fade: categories['تانية بنات'][2] }" @click="toggleCategory('تانية بنات', 2)"> القيامة 2</div>
        <div class="text" v-bind:class="{ fade: categories['تانية بنات'][3] }" @click="toggleCategory('تانية بنات', 3)"> القيامة 3</div>
        <div class="text" v-bind:class="{ fade: categories['تانية بنات'][4] }" @click="toggleCategory('تانية بنات', 4)">طقس</div>
        <div class="text" v-bind:class="{ fade: categories['تانية بنات'][5] }" @click="toggleCategory('تانية بنات', 5)">شخصيات كتابية</div>
        <div class="text" v-bind:class="{ fade: categories['تانية بنات'][6] }" @click="toggleCategory('تانية بنات', 6)">معلومات عامة</div>
      </div>
      <div class="categories" v-if="talta_welad">
        <div class="text" v-bind:class="{ fade: categories['تالتة ولاد'][1] }" @click="toggleCategory('تالتة ولاد', 1)"> القيامة 1</div>
        <div class="text" v-bind:class="{ fade: categories['تالتة ولاد'][2] }" @click="toggleCategory('تالتة ولاد', 2)"> القيامة 2</div>
        <div class="text" v-bind:class="{ fade: categories['تالتة ولاد'][3] }" @click="toggleCategory('تالتة ولاد', 3)">طقس</div>
        <div class="text" v-bind:class="{ fade: categories['تالتة ولاد'][4] }" @click="toggleCategory('تالتة ولاد', 4)">ألحان</div>
        <div class="text" v-bind:class="{ fade: categories['تالتة ولاد'][5] }" @click="toggleCategory('تالتة ولاد', 5)">الكتاب المقدس</div>
        <div class="text" v-bind:class="{ fade: categories['تالتة ولاد'][6] }" @click="toggleCategory('تالتة ولاد', 6)">معلومات عامة</div>
      </div>
      <div class="categories" v-if="talta_banat">
        <div class="text" v-bind:class="{ fade: categories['تالتة بنات'][1] }" @click="toggleCategory('تالتة بنات', 1)"> القيامة 1</div>
        <div class="text" v-bind:class="{ fade: categories['تالتة بنات'][2] }" @click="toggleCategory('تالتة بنات', 2)"> القيامة 2</div>
        <div class="text" v-bind:class="{ fade: categories['تالتة بنات'][3] }" @click="toggleCategory('تالتة بنات', 3)"> القيامة 3</div>
        <div class="text" v-bind:class="{ fade: categories['تالتة بنات'][4] }" @click="toggleCategory('تالتة بنات', 4)">طقس</div>
        <div class="text" v-bind:class="{ fade: categories['تالتة بنات'][5] }" @click="toggleCategory('تالتة بنات', 5)">شخصيات كتابية</div>
        <div class="text" v-bind:class="{ fade: categories['تالتة بنات'][6] }" @click="toggleCategory('تالتة بنات', 6)">معلومات عامة</div>
      </div>
    </div>
    <div class="scores-partition">
      <div></div>
      <div>
        <div style="color: white; font-weight: bold">أولى ولاد</div>
        <br>
        <div @click="open1b" class="jumping-object1b" :style="{ width: objectWidth + 'px', height: objectWidth + 'px', bottom: correctAnswers1b === totalScores ? maxHeight + 'px' : step * correctAnswers1b + 'px' }"></div>
      </div>
      <div>
        <div style="color: white; font-weight: bold">أولى بنات</div>
        <br>
        <div @click="open1g" class="jumping-object1g" :style="{ width: objectWidth + 'px', height: objectWidth + 'px', bottom: correctAnswers1g === totalScores ? maxHeight + 'px' : step * correctAnswers1g + 'px' }"></div>
      </div>
      <div>
        <div style="color: white; font-weight: bold">تانية ولاد</div>
        <br>
        <div @click="open2b" class="jumping-object2b" :style="{ width: objectWidth + 'px', height: objectWidth + 'px', bottom: correctAnswers2b === totalScores ? maxHeight + 'px' : step * correctAnswers2b + 'px' }"></div>
      </div>
      <div>
        <div style="color: white; font-weight: bold">تانية بنات</div>
        <br>
        <div @click="open2g" class="jumping-object2g" :style="{ width: objectWidth + 'px', height: objectWidth + 'px', bottom: correctAnswers2g === totalScores ? maxHeight + 'px' : step * correctAnswers2g + 'px' }"></div>
      </div>
      <div>
        <div style="color: white; font-weight: bold">تالتة ولاد</div>
        <br>
        <div @click="open3b" class="jumping-object3b" :style="{ width: objectWidth + 'px', height: objectWidth + 'px', bottom: correctAnswers3b === totalScores ? maxHeight + 'px' : step * correctAnswers3b + 'px' }"></div>
      </div>
      <div>
        <div style="color: white; font-weight: bold">تالتة بنات</div>
        <br>
        <div @click="open3g" class="jumping-object3g" :style="{ width: objectWidth + 'px', height: objectWidth + 'px', bottom: correctAnswers3g === totalScores ? maxHeight + 'px' : step * correctAnswers3g + 'px' }"></div>
      </div>
      <div></div>
    </div>
  </div>
</template>

<script>
import swal from 'sweetalert2';
export default {
  name: 'Quiz',
  props: {
    msg: String
  },
  data() {
    return {
      oula_welad: false,
      oula_banat: false,
      tanya_welad: false,
      tanya_banat: false,
      talta_welad: false,
      talta_banat: false,
      categories: {
        'أولى ولاد': {1: false, 2: false, 3: false, 4: false, 5: false, 6: false},
        'أولى بنات': {1: false, 2: false, 3: false, 4: false, 5: false, 6: false},
        'تانية ولاد': {1: false, 2: false, 3: false, 4: false, 5: false, 6: false},
        'تانية بنات': {1: false, 2: false, 3: false, 4: false, 5: false, 6: false},
        'تالتة ولاد': {1: false, 2: false, 3: false, 4: false, 5: false, 6: false},
        'تالتة بنات': {1: false, 2: false, 3: false, 4: false, 5: false, 6: false},
      },
      correctAnswers1b: 0,
      correctAnswers2b: 0,
      correctAnswers3b: 0,
      correctAnswers1g: 0,
      correctAnswers2g: 0,
      correctAnswers3g: 0,
      totalScores: 11, // number of points + 1
      maxHeight: 0,
      Questions: {
        'أولى ولاد': {
          1: {
            question: 'القيامة 1',
            answer: 'الجواب'
          },
          2: {
            question: 'القيامة 2',
            answer: 'الجواب'
          },
          3: {
            question: 'القيامة 3',
            answer: 'الجواب'
          },
          4: {
            question: 'طقس',
            answer: 'الجواب'
          },
          5: {
            question: 'الكتاب المقدس',
            answer: 'الجواب'
          },
          6: {
            question: 'معلومات عامة',
            answer: 'الجواب'
          }
        },
        'أولى بنات': {
          1: {
            question: 'القيامة 1',
            answer: 'الجواب'
          },
          2: {
            question: 'القيامة 2',
            answer: 'الجواب'
          },
          3: {
            question: 'القيامة 3',
            answer: 'الجواب'
          },
          4: {
            question: 'طقس',
            answer: 'الجواب'
          },
          5: {
            question: 'الكتاب المقدس',
            answer: 'الجواب'
          },
          6: {
            question: 'معلومات عامة',
            answer: 'الجواب'
          }
        },
        'تانية ولاد': {
          1: {
            question: `<span>من أنا؟ كنت مجرم مسجون و هتف الشعب بأسمي و في الاخر المسيح اخد مكاني</span><br><span>(يوسف الرامي - باراباس - بطرس)</span>`,
            answer: 'الجواب'
          },
          2: {
            question: 'القيامة 2',
            answer: 'الجواب'
          },
          3: {
            question: 'القيامة 3',
            answer: 'الجواب'
          },
          4: {
            question: 'طقس',
            answer: 'الجواب'
          },
          5: {
            question: 'الكتاب المقدس',
            answer: 'الجواب'
          },
          6: {
            question: 'معلومات عامة',
            answer: 'الجواب'
          }
        },
        'تانية بنات': {
          1: {
            question: 'القيامة 1',
            answer: 'الجواب'
          },
          2: {
            question: 'القيامة 2',
            answer: 'الجواب'
          },
          3: {
            question: 'القيامة 3',
            answer: 'الجواب'
          },
          4: {
            question: 'طقس',
            answer: 'الجواب'
          },
          5: {
            question: 'الكتاب المقدس',
            answer: 'الجواب'
          },
          6: {
            question: 'معلومات عامة',
            answer: 'الجواب'
          }
        },
        'تالتة ولاد': {
          1: {
            question: 'من انا؟ انا من الرامة و كنت غني جدا و قعد المسيح في ممتلكاتي 3 ايام',
            answer: 'يوسف الرامي'
          },
          2: {
            question: 'من أنا؟ كنت مجرم مسجون و هتف الشعب بأسمي و في الاخر المسيح اخد مكاني',
            answer: 'باراباس'
          },
          3: {
            question: 'ما الذي يفعله أبونا في القداس يشير الى دحرجة الحجر عن القبر؟',
            answer: 'رفع الابروسفارين'
          },
          4: {
            question: 'نقول في الهيتنيات ان مبوق القيامة هو اول من أعلن عن قيامة المسيح فمن هو؟',
            answer: 'الملاك ميخائيل'
          },
          5: {
            question: ' القصة اللي في سفر الخروج بتشير الى صلب المسيح هي ـــــ و اللي اتاخد منها تسمية بصخة اللي معناها ـــــ',
            answer: 'خروف الفصح - عبور'
          },
          6: {
            question: 'من أي ماده يتم تصنيع الزجاج',
            answer: 'الرمال'
          }
        },
        'تالتة بنات': {
          1: {
            question: 'القيامة 1',
            answer: 'الجواب'
          },
          2: {
            question: 'القيامة 2',
            answer: 'الجواب'
          },
          3: {
            question: 'القيامة 3',
            answer: 'الجواب'
          },
          4: {
            question: 'طقس',
            answer: 'الجواب'
          },
          5: {
            question: 'الكتاب المقدس',
            answer: 'الجواب'
          },
          6: {
            question: 'معلومات عامة',
            answer: 'الجواب'
          }
        },

      }
      
    }
  },
  created() {
    this.maxHeight = window.innerHeight - 5;
  },
  computed: {
    step() {
      return this.maxHeight / this.totalScores;
    },
    objectWidth() {
      return 0.0351493848857645 * window.innerWidth;
    },
  },
  methods: {
    toggleCategory(team, index) {
      let q = this.Questions[team][index].question;
      let ans = this.Questions[team][index].answer;
      swal.fire({
        width: '800px',
        height: '500px',
        title: `<span style="font-size: 50px; font-weight: bold">${q}</span>`,
        confirmButtonText: "الاجابة",
      }).then((result) => {
        if (result.isConfirmed) {
          swal.fire(`<span style="font-size: 50px; font-weight: bold">${ans}</span>`);
        }
      });
      this.categories[team][index] = true;
      const categoryDiv = document.querySelector('.categories > *:nth-child(' + index + ')');
      if (this.categories[team][index]) {
        categoryDiv.classList.add('fade');
      }
    },
    fadeOthers(event) {
      const teamsDiv = document.querySelector('.teams');
      const children = teamsDiv.children;
      for (let i = 0; i < children.length; i++) {
        if (children[i] !== event.target) {
          children[i].classList.add('fade');
        } else {
          children[i].classList.remove('fade');
        }
      }
      this.oula_welad = false;
      this.oula_banat = false;
      this.tanya_welad = false;
      this.tanya_banat = false;
      this.talta_welad = false;
      this.talta_banat = false;
      if (event.target.textContent === 'أولى ولاد') {
        this.oula_welad = true;
      } else if (event.target.textContent === 'أولى بنات') {
        this.oula_banat = true;
      } else if (event.target.textContent === 'تانية ولاد') {
        this.tanya_welad = true;
      } else if (event.target.textContent === 'تانية بنات') {
        this.tanya_banat = true;
      } else if (event.target.textContent === 'تالتة ولاد') {
        this.talta_welad = true;
      } else if (event.target.textContent === 'تالتة بنات') {
        this.talta_banat = true;
      }
    },
    Winner(){
      var audio = new Audio("https://audio.code.org/goal1.mp3");
      audio.play();
    },
    Loser(){
      var audio = new Audio("https://audio.code.org/losepoint2.mp3");
      audio.play();
    },
    open1b(){
      swal.fire({
        title: "أولى ولاد",
        showDenyButton: true,
        showCancelButton: false,
        confirmButtonText: `<span style="font-size: 30px; font-weight: bold">&#43;</span>`,
        denyButtonText: `<span style="font-size: 30px; font-weight: bold">&#8722;</span>`,
      }).then((result) => {
        if (result.isConfirmed) {
          this.answerQuestion1b(true);
          this.Winner();
        } else if (result.isDenied) {
          this.decreaseAnswer1b();
          this.Loser();
        }
      });
    },
    open2b(){
      swal.fire({
        title: "تانية ولاد",
        showDenyButton: true,
        showCancelButton: false,
        confirmButtonText: `<span style="font-size: 30px; font-weight: bold">&#43;</span>`,
        denyButtonText: `<span style="font-size: 30px; font-weight: bold">&#8722;</span>`,
      }).then((result) => {
        if (result.isConfirmed) {
          this.answerQuestion2b(true);
          this.Winner();
        } else if (result.isDenied) {
          this.decreaseAnswer2b();
          this.Loser();
        }
      });
    },
    open3b(){
      swal.fire({
        title: "تالتة ولاد",
        showDenyButton: true,
        showCancelButton: false,
        confirmButtonText: `<span style="font-size: 30px; font-weight: bold">&#43;</span>`,
        denyButtonText: `<span style="font-size: 30px; font-weight: bold">&#8722;</span>`,
      }).then((result) => {
        if (result.isConfirmed) {
          this.answerQuestion3b(true);
          this.Winner();
        } else if (result.isDenied) {
          this.decreaseAnswer3b();
          this.Loser();
        }
      });
    },
    open1g(){
      swal.fire({
        title: "أولى بنات",
        showDenyButton: true,
        showCancelButton: false,
        confirmButtonText: `<span style="font-size: 30px; font-weight: bold">&#43;</span>`,
        denyButtonText: `<span style="font-size: 30px; font-weight: bold">&#8722;</span>`,
      }).then((result) => {
        if (result.isConfirmed) {
          this.answerQuestion1g(true);
          this.Winner();
        } else if (result.isDenied) {
          this.decreaseAnswer1g();
          this.Loser();
        }
      });
    },
    open2g(){
      swal.fire({
        title: "تانية بنات",
        showDenyButton: true,
        showCancelButton: false,
        confirmButtonText: `<span style="font-size: 30px; font-weight: bold">&#43;</span>`,
        denyButtonText: `<span style="font-size: 30px; font-weight: bold">&#8722;</span>`,
      }).then((result) => {
        if (result.isConfirmed) {
          this.answerQuestion2g(true);
          this.Winner();
        } else if (result.isDenied) {
          this.decreaseAnswer2g();
          this.Loser();
        }
      });
    },
    open3g(){
      swal.fire({
        title: "تالتة بنات",
        showDenyButton: true,
        showCancelButton: false,
        confirmButtonText: `<span style="font-size: 30px; font-weight: bold">&#43;</span>`,
        denyButtonText: `<span style="font-size: 30px; font-weight: bold">&#8722;</span>`,
      }).then((result) => {
        if (result.isConfirmed) {
          this.answerQuestion3g(true);
          this.Winner();
        } else if (result.isDenied) {
          this.decreaseAnswer3g();
          this.Loser();
        }
      });
    },
    answerQuestion1b(isCorrect) {
      if (isCorrect) {
        if (this.correctAnswers1b === this.totalScores - 1) {
          return;
        }
        this.correctAnswers1b++;
        const jumpingObject = document.querySelector('.jumping-object1b');
        jumpingObject.classList.remove('jump');
        void jumpingObject.offsetWidth;
        jumpingObject.classList.add('jump');
      }
    },
    decreaseAnswer1b() {
      if (this.correctAnswers1b > 0) {
        this.correctAnswers1b--;
        const jumpingObject = document.querySelector('.jumping-object1b');
        jumpingObject.classList.remove('jump');
        void jumpingObject.offsetWidth;
        jumpingObject.classList.add('jump');
      }
    },
    answerQuestion2b(isCorrect) {
      if (isCorrect) {
        if (this.correctAnswers2b === this.totalScores - 1) {
          return;
        }
        this.correctAnswers2b++;
        const jumpingObject = document.querySelector('.jumping-object2b');
        jumpingObject.classList.remove('jump');
        void jumpingObject.offsetWidth;
        jumpingObject.classList.add('jump');
      }
    },
    decreaseAnswer2b() {
      if (this.correctAnswers2b > 0) {
        this.correctAnswers2b--;
        const jumpingObject = document.querySelector('.jumping-object2b');
        jumpingObject.classList.remove('jump');
        void jumpingObject.offsetWidth;
        jumpingObject.classList.add('jump');
      }
    },
    answerQuestion3b(isCorrect) {
      if (isCorrect) {
        if (this.correctAnswers3b === this.totalScores - 1) {
          return;
        }
        this.correctAnswers3b++;
        const jumpingObject = document.querySelector('.jumping-object3b');
        jumpingObject.classList.remove('jump');
        void jumpingObject.offsetWidth;
        jumpingObject.classList.add('jump');
      }
    },
    decreaseAnswer3b() {
      if (this.correctAnswers3b > 0) {
        this.correctAnswers3b--;
        const jumpingObject = document.querySelector('.jumping-object3b');
        jumpingObject.classList.remove('jump');
        void jumpingObject.offsetWidth;
        jumpingObject.classList.add('jump');
      }
    },
    answerQuestion1g(isCorrect) {
      if (isCorrect) {
        if (this.correctAnswers1g === this.totalScores - 1) {
          return;
        }
        this.correctAnswers1g++;
        const jumpingObject = document.querySelector('.jumping-object1g');
        jumpingObject.classList.remove('jump');
        void jumpingObject.offsetWidth;
        jumpingObject.classList.add('jump');
      }
    },
    decreaseAnswer1g() {
      if (this.correctAnswers1g > 0) {
        this.correctAnswers1g--;
        const jumpingObject = document.querySelector('.jumping-object1g');
        jumpingObject.classList.remove('jump');
        void jumpingObject.offsetWidth;
        jumpingObject.classList.add('jump');
      }
    },
    answerQuestion2g(isCorrect) {
      if (isCorrect) {
        if (this.correctAnswers2g === this.totalScores - 1) {
          return;
        }
        this.correctAnswers2g++;
        const jumpingObject = document.querySelector('.jumping-object2g');
        jumpingObject.classList.remove('jump');
        void jumpingObject.offsetWidth;
        jumpingObject.classList.add('jump');
      }
    },
    decreaseAnswer2g() {
      if (this.correctAnswers2g > 0) {
        this.correctAnswers2g--;
        const jumpingObject = document.querySelector('.jumping-object2g');
        jumpingObject.classList.remove('jump');
        void jumpingObject.offsetWidth;
        jumpingObject.classList.add('jump');
      }
    },
    answerQuestion3g(isCorrect) {
      if (isCorrect) {
        if (this.correctAnswers3g === this.totalScores - 1) {
          return;
        }
        this.correctAnswers3g++;
        const jumpingObject = document.querySelector('.jumping-object3g');
        jumpingObject.classList.remove('jump');
        void jumpingObject.offsetWidth;
        jumpingObject.classList.add('jump');
      }
    },
    decreaseAnswer3g() {
      if (this.correctAnswers3g > 0) {
        this.correctAnswers3g--;
        const jumpingObject = document.querySelector('.jumping-object3g');
        jumpingObject.classList.remove('jump');
        void jumpingObject.offsetWidth;
        jumpingObject.classList.add('jump');
      }
    },
  }
}
</script>

<style scoped>
div img {
  max-width: 100%;
  max-height: 100%;
}
.text{
  display: flex;
  align-items: center;
  justify-content: center;
}
.main-class {
  display: flex;
  justify-content: space-around;
  width: 99%;
}

.question-partition {
  flex: 0 0 63%;
  display: flex;
  justify-content: space-around;
  flex-direction: column;

}
.teams{
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  font-weight: bold;
}
.teams :nth-child(1){
  padding: 2.5%;
  background: rgba(9, 106, 10, 0.74);
  backdrop-filter: blur();
  color: white;
  border-radius: 20px;
  font-size: 130%;
}

.teams :nth-child(2){
  padding: 2.5%;
  background: rgba(150, 7, 7, 0.74);
  backdrop-filter: blur();
  color: white;
  border-radius: 20px;
  font-size: 130%;
}

.teams :nth-child(3){
  padding: 2.5%;
  background: rgba(12, 94, 165, 0.74);
  backdrop-filter: blur();
  color: white;
  border-radius: 20px;
  font-size: 130%;
}

.teams :nth-child(4){
  padding: 2.5%;
  background: rgba(240, 110, 200, 0.74);
  backdrop-filter: blur();
  color: white;
  border-radius: 20px;
  font-size: 130%;
}

.teams :nth-child(5){
  padding: 2.5%;
  background: rgba(227, 65, 15, 0.74);
  backdrop-filter: blur();
  color: white;
  border-radius: 20px;
  font-size: 130%;
}

.teams :nth-child(6){
  padding: 2.5%;
  background: rgba(196, 167, 7, 0.74);
  backdrop-filter: blur();
  color: white;
  border-radius: 20px;
  font-size: 130%;
}

.teams :hover{
  cursor: pointer;
}

.categories{
  flex: 0 0 70%;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around
}

.categories > * {
  flex: 1 0 150pt;
  height: 150pt;
  padding: 2.5%;
  background: rgba(0, 0, 0, 0.74);
  backdrop-filter: blur();
  color: white;
  border-radius: 20px;
  font-size: 200%;
  margin: 1%;
  text-align: center;
  font-weight: bold;

}
.categories :hover{
  cursor: pointer;
}

.scores-partition {
  flex: 0 0 37%;
  display: flex;
  justify-content: space-evenly;
  align-items: flex-end;
  height: 98vh;
  background: #292525;
  background: url(road.png) repeat;
  background-size: calc(100% / 7);
}

.jumping-object1b{
  position: relative;
  margin-bottom: 5px;
  background: url(car3.png);
  transition: bottom 1s ease-in-out;
  background-size:100%;
}
.jumping-object2b{
  position: relative;
  margin-bottom: 5px;
  background: url(car2.png);
  transition: bottom 1s ease-in-out;
  background-size:100%;
}
.jumping-object3b{
  position: relative;
  margin-bottom: 5px;
  background: url(car1.png);
  transition: bottom 1s ease-in-out;
  background-size:100%;
}
.jumping-object1g{
  position: relative;
  margin-bottom: 5px;
  background: url(car4.png);
  transition: bottom 1s ease-in-out;
  background-size:100%;
}
.jumping-object2g{
  position: relative;
  margin-bottom: 5px;
  background: url(car5.png);
  transition: bottom 1s ease-in-out;
  background-size:100%;
}
.jumping-object3g{
  position: relative;
  margin-bottom: 5px;
  background: url(car6.png);
  transition: bottom 1s ease-in-out;
  background-size:100%;
}
.jumping-object3g:hover{
  cursor: pointer;
}
.jumping-object3b:hover{
  cursor: pointer;
}
.jumping-object2g:hover{
  cursor: pointer;
}
.jumping-object2b:hover{
  cursor: pointer;
}
.jumping-object1g:hover{
  cursor: pointer;
}
.jumping-object1b:hover{
  cursor: pointer;
}
.fade {
  opacity: 0.5;
  transition: opacity 0.5s ease;
}
</style>


